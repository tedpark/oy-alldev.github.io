---
layout: main
main: true
title: 채용정보
description: 올디브에서 모히또 한잔?
---

<div class="loading-animation">
    <div class="recruit">
        <div class="title">올디브는 이런 분을 모시고 싶어요.</div>
         <div class="want">
            <ul>
                <li><div>스크럼과 코드 리뷰에 거부감이 없으신 분</div></li>
                <li><div>새로운 기술을 습득하고 적용하는 것에 즐거움을 느끼시는 분</div></li>
                <li><div>자신의 발자취를 문서로 남기는 것이 익숙하신 분</div></li>
                <li><div>부드러운 대화와 적극적인 토론이 즐거우신 분</div></li>
                <li><div>연차 보다는 가능성을 많이 품고 계시는 분</div></li>
            </ul>
        </div>
        <div class="title">채용 프로세스</div>
        <div class="process">
            <ul class="list">
                <li class="resume">
                    <div class="text-wrapper">01<br><span>서류전형</span></div>
                </li>
                <li class="interview1">
                    <div class="text-wrapper">02<br><span>기술 Track 인터뷰</span></div>
                </li>
                <li class="interview2">
                    <div class="text-wrapper">03<br><span> 인터뷰</span></div>
                </li>
                 <li class="interview2">
                                    <div class="text-wrapper">03<br><span>2차 인터뷰</span></div>
                                </li>
                <li class="final">
                    <div class="text-wrapper">04<br><span>최종 합격</span></div>
                </li>
            </ul>
            <div>올리브영의 기술 Track 면접은 CJAT 인성검사와 실무진이 참여하는 심층 면접으로 이루어져 있습니다. </div>
        </div>
        <div class="title">복지제도</div>
        <ul>
            {% for welfare in site.data.welfares %}
                <li class="welfare">
                    <div class="index">{{welfare.title}}</div>
                        <div class="section">
                            {% for content in welfare.contents %}
                                  <dikv class="sub_title">{{content.title}}</dikv>
                                  <div class="sub_description">{{content.description}}</div>
                            {% endfor %}
                        </div>
                </li>
            {% endfor %}       
        </ul>
    
</div>
</div>