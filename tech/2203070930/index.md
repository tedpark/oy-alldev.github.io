---
layout: post
type: tech
date: 2022-03-07 09:30
category: Friday Tech Session
title: Next.js 배포를 어떻게 할 것인가
subtitle: Next.js 가 SSR 로 사용하는 Node.js 에 대한 설명을 하려고 합니다.
writer: 835127
post-header: false
header-img: img/thumbnail.png
hash-tag: [deploy, nodejs, SSR, thread]
---
- ## Prologue

&nbsp;&nbsp;&nbsp; 올리브영의 front end 는 Renewal 중입니다.

&nbsp;&nbsp;&nbsp; 다들 아시는 Next.js 로의 전환 작업을 하고 있습니다.

&nbsp;&nbsp;&nbsp; 기존의 서버로 부터 front end 를 분리 하는 작업을 하고 있습니다.

&nbsp;&nbsp;&nbsp; 이번 포스팅은  Next.js 배포를 어떻게 할 것인가와 Next.js 가 SSR 로 사용하는 Node.js 에 대한 설명을 하려고 합니다.

&nbsp;&nbsp;&nbsp; 이어서 멀쓰(멀티쓰레드), 멀프(멀티프로세스) 에 대해서도, 그리고 다른 서버들도 살펴 보려고 합니다. erlang(=elixir) 같은 거요.


<br/>

- ## Deploy

&nbsp;&nbsp;&nbsp; 먼저 배포는 k8s + Docker PM2 로 배포를 합니다.

&nbsp;&nbsp;&nbsp;Node.js 는 Single Thread 기반의

&nbsp;&nbsp;&nbsp; JavaScript runtime built on [Chrome's V8 JavaScript engine](https://v8.dev/) 입니다.

&nbsp;&nbsp;&nbsp; 여기에서 js 가 실행되면 html 을 return 하는 구조가 Next.js 입니다.

&nbsp;&nbsp;&nbsp; PM2 는 CPU CORE 수에 맞게 node process 를 실행 및 관리를 하고, Multi Core 에 대응을 하고.

&nbsp;&nbsp;&nbsp; 예를 들어 CPU 가 8개이면 8개 실행 시켜 줍니다.

&nbsp;&nbsp;&nbsp; node process 가 죽으면 살려 줍니다.

&nbsp;&nbsp;&nbsp; 이와 별개로 k8s 도 Pod 이 죽으면 역시 바로 생성 합니다.

&nbsp;&nbsp;&nbsp; [PM2 - Process Management (keymetrics.io)](https://pm2.keymetrics.io/docs/usage/process-management/)

&nbsp;&nbsp;&nbsp; 특별한 건 없지요.

<br/>


- ## Multi Process 와 Multi Thread

&nbsp;&nbsp;&nbsp; 앞서 Node.js 가 Single Thread 기반이라고 말씀 드렸잖아요.

&nbsp;&nbsp;&nbsp; 그럼 Process 와 Thread 는 뭘까요.

&nbsp;&nbsp;&nbsp; Process 란 여러 독립된 Thread 를 가지고 있는 큰 단위 입니다.

&nbsp;&nbsp;&nbsp; Thread 란 Process 보다 작은 단위 입니다.

&nbsp;&nbsp;&nbsp; 거기에 Multi 가 붙으면 뭐가 달라질까요.

&nbsp;&nbsp;&nbsp; 멀티 스레드는 멀티 프로세스보다 적은 메모리 공간을 차지하고 `Context Switching`이 빠른 장점이 있지만, 

&nbsp;&nbsp;&nbsp; 동기화 문제와 하나의 스레드 장애로 전체 스레드가 종료 될 위험을 갖고 있다.

<br/>

&nbsp;&nbsp;&nbsp; 멀티 프로세스는 하나의 프로세스가 죽더라도 다른 프로세스에 영향을 주지 않아 안정성이 높지만, 

&nbsp;&nbsp;&nbsp; 멀티 스레드보다 많은 메모리공간과 CPU 시간을 차지하는 단점이 있다.

&nbsp;&nbsp;&nbsp; 라고 합니다.

<br/>

&nbsp;&nbsp;&nbsp; Multi Process 가 사실 개발자 입장에선 제일 좋지만, 성능 탓에  Multi Thread 를 사용한다 가 되겠습니다.

&nbsp;&nbsp;&nbsp; 물론 이걸 깬 light process 를 활용한 erlang(=Elixir) 도 있습니다.

&nbsp;&nbsp;&nbsp; 더 아래에서 살펴 보겠습니다.

<br/>

&nbsp;&nbsp;&nbsp; 그렇다면 Single Thread 만을 사용 하고 성능을 높이면 어떻겠니? 에서 출발한

&nbsp;&nbsp;&nbsp; Nginx, Node.js(=express.js) 얘네들은 Single Thread 로 요청을 처리 합니다.

&nbsp;&nbsp;&nbsp; Apache 대비 Nginx 는 두배정도 처리를 더 하고 있습니다.

&nbsp;&nbsp;&nbsp; [Apache Vs NGINX – Which Is The Best Web Server for You? (serverguy.com)](https://serverguy.com/comparison/apache-vs-nginx/)

<br/>

&nbsp;&nbsp;&nbsp; 멀티 쓰레드가 성능상 좋은데, 여러 문제가 많아 싱글쓰레드로 성능을 높였다면,

&nbsp;&nbsp;&nbsp; 멀티 프로세스의 CPU 와 Memory 를 light 하게 가져가면 어떨까요? 에서 출발한게

&nbsp;&nbsp;&nbsp; Erlang(=Elixir) 의 BEAM 입니다.

&nbsp;&nbsp;&nbsp; java 의 JVM 과 같습니다.

<br/>

&nbsp;&nbsp;&nbsp; Erlang(=Elixir) 의 BEAM 은 거기에 한 걸음 더 나아가 오래 걸리는 작업은 뒤로 빼버립니다.

&nbsp;&nbsp;&nbsp; Scheduler 가 BEAM 에 포함되어 있습니다.

&nbsp;&nbsp;&nbsp; The JVM is built for parallelism, the BEAM for concurrency

&nbsp;&nbsp;&nbsp; [Why Elixir? Throughput. on Vimeo](https://vimeo.com/370545381)

<br/>

- ## 시작한거 parallelism concurrency 갑시다.

&nbsp;&nbsp;&nbsp; ![1_uXskTJltvUHAPDa0gNV9iw.png](https://miro.medium.com/max/1400/1*X14b2Clrv0kgSNqcvwFUdg.png)

&nbsp;&nbsp;&nbsp; ![1_X14b2Clrv0kgSNqcvwFUdg.png](https://miro.medium.com/max/1400/1*uXskTJltvUHAPDa0gNV9iw.png)

&nbsp;&nbsp;&nbsp; ![1_EpzvhxXSe94sBtodSOQw6g.png](https://miro.medium.com/max/1400/1*EpzvhxXSe94sBtodSOQw6g.png)

&nbsp;&nbsp;&nbsp; 참 쉽죠?

&nbsp;&nbsp;&nbsp; [Elixir and The Beam: How Concurrency Really Works  by Sophie DeBenedetto  Flatiron Labs  Medium](https://medium.com/flatiron-labs/elixir-and-the-beam-how-concurrency-really-works-3cc151cddd61)

<br/>

1. Best

⇒ Elixir 와 BEAM 은 최강인가.

[Phoenix Framework](https://www.phoenixframework.org/)

<a src="https://github.com/tedpark/elixir_with_mongo_example">https://github.com/tedpark/elixir_with_mongo_example</a>

<br/>

⇒ Akka Scala 는 최강인가.

[Lagom - Home (lagomframework.com)](https://www.lagomframework.com/documentation/1.6.x/scala/Home.html)

[Akka: build concurrent, distributed, and resilient message-driven applications for Java and Scala Akka](https://akka.io/)

<br/>

⇒ Clojure 가 최강인가.

[Kit Framework (kit-clj.github.io)](https://kit-clj.github.io/)

[Luminus - a Clojure web framework (luminusweb.com)](https://luminusweb.com/)

<br/>

⇒ Rust Actor 가 최강인가.

[Actix Web A powerful, pragmatic, and extremely fast web framework for Rust.](https://actix.rs/)

<br/>

다 상황에 맞게 쓰면 됩니다.

<br/>

저는 Rust Actor(Actix) + MongoDB, Elixir Phoenix <a src="https://github.com/tedpark/elixir_with_mongo_example">https://github.com/tedpark/elixir_with_mongo_example</a> + MongoDB

사용 중이고, A.I. 때문에 Python FastAPI 도 사용중입니다.

<br/>

---

<br/>

다음 포스팅 예고. A.I. NLP 입니다.

1. NLP 는 아래의 강좌 4개를 보시면 전체적인 흐름을 파악 하는데 도움이 될겁니다. 순서대로 이며,

   시간이 없으신 분들은 3강, 4강 정도만 보셔도 큰 도움이 될겁니다.

2. <a src="https://github.com/kiyoungkim1/ReadyToUseAI">https://github.com/kiyoungkim1/ReadyToUseAI</a>

3. <a src="https://www.youtube.com/watch?v=Z201jwWo-xs&t=762s">https://www.youtube.com/watch?v=Z201jwWo-xs&t=762s</a>

4. <a src="https://www.youtube.com/watch?v=5ivVf-Guqk4&t=1137s">https://www.youtube.com/watch?v=5ivVf-Guqk4&t=1137s</a>

5. <a src="https://www.youtube.com/watch?v=9HDBKS4j64M">https://www.youtube.com/watch?v=9HDBKS4j64M</a>

6. <a src="https://www.youtube.com/watch?v=sSy8ufyiuDY">https://www.youtube.com/watch?v=sSy8ufyiuDY</a>

7. <a src="https://github.com/pytorch/fairseq 를 사용했습니다.">https://github.com/pytorch/fairseq 를 사용했습니다.</a>

8. <a src="https://woongjun-warehouse.tistory.com/2">https://woongjun-warehouse.tistory.com/2</a>

p.s. 함께 하고 싶은 분들의 문은 blah blah. 일단 좀 도와 주십시오!!


이상입니다.
