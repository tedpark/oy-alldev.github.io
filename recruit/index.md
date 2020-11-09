---
layout: main
main: true
title: 채용정보
---

<div class="loading-animation">
    <div class="recruit">
        <div class="title">올디브는 이런 분을 모시고 싶어요.</div>
         <div class="want">
            <ul>
                <li><div><span class="emoji">✓&nbsp;</span>스크럼과 코드 리뷰에 거부감이 없으신 분</div></li>
                <li><div><span class="emoji">✓&nbsp;</span>새로운 기술을 습득하고 적용하는 것에 즐거움을 느끼시는 분</div></li>
                <li><div><span class="emoji">✓&nbsp;</span>자신의 발자취를 문서로 남기는 것이 익숙하신 분</div></li>
                <li><div><span class="emoji">✓&nbsp;</span>부드러운 대화와 적극적인 토론이 즐거우신 분</div></li>
                <li><div><span class="emoji">✓&nbsp;</span>연차 보다는 가능성을 많이 품고 계시는 분</div></li>
            </ul>
        </div>
        <div class="title">채용 프로세스</div>
        <div class="process">
            <ul class="list">
                {% for process in site.data.recruitProcess %}
                      <li class="transition">
                          <div class="label"><span>0{{process.index}}</span><br>{{process.label}}</div>
                          <p class="description">{{process.description}}</p>
                      </li>         
                {% endfor %}  
             </ul>
        </div>
        <div class="title">복지제도</div>
        <ul>
            {% for welfare in site.data.welfares %}
                <li class="welfare">
                    <div class="index">{{welfare.title}}</div>
                        <div class="section">
                            {% for content in welfare.contents %}
                                  <div class="sub_title">{{content.title}}</div>
                                  <div class="description">{{content.description}}</div>
                                  <div class="sub_description">{{content.sub_description}}</div>
                            {% endfor %}
                    </div>
                </li>
            {% endfor %}       
        </ul>
    
</div>
</div>