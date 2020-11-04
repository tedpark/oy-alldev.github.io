---
layout: post
type: tech
date: 2020-11-02 18:46bcv
category: Server
title: Slack으로 AWS 모니터링하기
subtitle: 👀 AWS Lambda를 활용하여 Slack에서 CloudWatch 모니터링
writer: 834588
post-header: true
header-img: "img/about.jpg"
---


AWS EC2 인스턴스에서 taining이 끝나고나면 90% 이상 치솟던 CPU 할당량이 0%로 수렴하게 되는데, 이 때 training이 끝났다는 알림 메시지를 받고 싶었습니다.

![](img/07.png)

<figcaption>토글을 활성화하고, Add New Webhook to Workspace 클릭</figcaption>

Activate Incoming Webhooks 설정을 `on`으로 활성화하면, 아래처럼 가이드가 뜹니다. 이 중에 최하단의 Add New Webook to Workspace 버튼을 클릭합니다.
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Lorem mollis aliquam ut porttitor. Tincidunt tortor aliquam nulla facilisi cras fermentum odio eu. Egestas sed sed risus pretium quam vulputate. Pharetra magna ac placerat vestibulum lectus mauris ultrices eros in. Sit amet massa vitae tortor condimentum lacinia. Lobortis feugiat vivamus at augue eget. Nibh mauris cursus mattis molestie a iaculis. Viverra orci sagittis eu volutpat odio facilisis mauris sit. Blandit turpis cursus in hac. Pharetra diam sit amet nisl. Adipiscing elit pellentesque habitant morbi tristique senectus et netus et. Massa id neque aliquam vestibulum morbi blandit. Risus in hendrerit gravida rutrum quisque non tellus orci. Suspendisse sed nisi lacus sed viverra. Id ornare arcu odio ut sem nulla pharetra diam sit. Elementum pulvinar etiam non quam lacus suspendisse faucibus. Enim eu turpis egestas pretium aenean pharetra magna. Phasellus vestibulum lorem sed risus ultricies tristique nulla aliquet.

Quis viverra nibh cras pulvinar. Morbi tristique senectus et netus et malesuada. Lectus urna duis convallis convallis tellus. Eget aliquet nibh praesent tristique magna sit amet. Ullamcorper velit sed ullamcorper morbi. Turpis egestas maecenas pharetra convallis posuere morbi. Dignissim convallis aenean et tortor at risus viverra adipiscing at. Sit amet mauris commodo quis imperdiet massa tincidunt. Fermentum posuere urna nec tincidunt praesent semper feugiat. Blandit cursus risus at ultrices mi tempus imperdiet nulla. Sed augue lacus viverra vitae congue eu consequat. Odio morbi quis commodo odio aenean sed adipiscing diam donec. Commodo quis imperdiet massa tincidunt nunc pulvinar sapien. A iaculis at erat pellentesque adipiscing commodo elit. Sodales neque sodales ut etiam. Tellus mauris a diam maecenas sed enim ut sem.

Volutpat lacus laoreet non curabitur. Semper risus in hendrerit gravida rutrum. Ac turpis egestas sed tempus urna. Tortor at risus viverra adipiscing at in tellus integer. Sed risus ultricies tristique nulla aliquet enim tortor. Aliquet risus feugiat in ante metus dictum at tempor. Feugiat scelerisque varius morbi enim nunc faucibus a pellentesque sit. Risus sed vulputate odio ut enim blandit volutpat maecenas volutpat. Senectus et netus et malesuada fames. Donec pretium vulputate sapien nec sagittis aliquam. Risus nullam eget felis eget. Convallis a cras semper auctor neque vitae tempus quam. Commodo viverra maecenas accumsan lacus vel. Mattis nunc sed blandit libero. In est ante in nibh mauris. Facilisis sed odio morbi quis. Vitae auctor eu augue ut lectus arcu bibendum at varius.

Et malesuada fames ac turpis egestas sed tempus urna. Libero nunc consequat interdum varius sit amet mattis vulputate. Donec massa sapien faucibus et molestie ac feugiat sed lectus. Cras fermentum odio eu feugiat. In hac habitasse platea dictumst quisque sagittis purus sit amet. Nunc consequat interdum varius sit amet mattis vulputate enim. Posuere ac ut consequat semper viverra nam libero justo. Ut lectus arcu bibendum at varius. Ornare massa eget egestas purus viverra accumsan in. Ornare arcu dui vivamus arcu felis bibendum ut tristique. Urna duis convallis convallis tellus. Vestibulum morbi blandit cursus risus at ultrices. Habitant morbi tristique senectus et netus et malesuada fames.

Tristique senectus et netus et malesuada. Posuere morbi leo urna molestie at elementum eu. Libero justo laoreet sit amet. Eleifend mi in nulla posuere. Iaculis nunc sed augue lacus. Sodales ut etiam sit amet nisl purus in mollis. Eget nulla facilisi etiam dignissim diam quis. Mi ipsum faucibus vitae aliquet nec ullamcorper sit. Ac turpis egestas integer eget aliquet. Volutpat consequat mauris nunc congue nisi vitae suscipit. Proin sagittis nisl rhoncus mattis rhoncus urna neque. Facilisi cras fermentum odio eu feugiat pretium. Non sodales neque sodales ut etiam sit amet. Accumsan in nisl nisi scelerisque eu ultrices vitae auctor eu. Adipiscing elit duis tristique sollicitudin nibh sit amet commodo. In iaculis nunc sed augue lacus viverra vitae congue eu. Sodales ut etiam sit amet nisl purus in. Mauris nunc congue nisi vitae. Enim praesent elementum facilisis leo vel fringilla.