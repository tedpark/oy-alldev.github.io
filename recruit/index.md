---
layout: main
main: true
title: 채용정보
---

<div class="loading-animation">
    <div class="recruit">
        <div class="section want">
            <div class="title">올디브는 이런 분을 모시고 싶어요.</div>
             <div class="content">
                <ul>
                    <li>스크럼과 코드 리뷰에 거부감이 없으신 분</li>
                    <li>새로운 기술을 습득하고 적용하는 것에 즐거움을 느끼시는 분</li>
                    <li>자신의 발자취를 문서로 남기는 것이 익숙하신 분</li>
                    <li>부드러운 대화와 적극적인 토론이 즐거우신 분</li>
                    <li>연차 보다는 가능성을 많이 품고 계시는 분</li>
                </ul>
            </div>
        </div>
        <div class="section process">
            <div class="title">상시 채용 프로세스</div>
            <div class="content">
                <div class="list">
                    {% for process in site.data.recruit-process %}
                    <div class="process-item">
                        <div class="circle {% if process.detail != nil %}has-detail{% endif %}">
                            <div class="text-wrapper">
                                <div class="index">0{{process.index}}</div>
                                <div class="label">{{process.label}}</div>
                                {% if process.detail != nil %}
                                <ul class="detail">
                                    {% for detail in process.detail %}
                                    <li>{{ detail }}</li>                            
                                    {% endfor %}
                                </ul>
                                {% endif %}
                            </div>
                        </div>
                        <div class="description">
                            {{process.description}}
                        </div>
                    </div>
                    {% endfor %}
                </div>
            </div>
        </div>
        <div class="section welfare culture">
            <div class="title">개발팀의 문화</div>
            <div class="content">
                <div class="card-list">
                    {% for welfare in site.data.welfares %}
                    {% if welfare.type == 'alldev' %}
                    <div class="card">
                        <div class="title">
                            <span class="emoji">{{welfare.emoji}}</span>
                            {{welfare.title}}
                        </div>
                        <div class="subtitle">{{welfare.subtitle}}</div>
                        <div class="description">
                            <ul>
                                {% for description in welfare.description %}
                                <li class="item">{{description}}</li>
                                {% endfor %}
                            </ul>
                        </div>
                    </div>
                    {% endif %}
                    {% endfor %}   
                </div>  
            </div>
        </div>
        <div class="section welfare">
            <div class="title">사내 복지제도</div>
            <div class="content">
                <div class="card-list">
                    {% for welfare in site.data.welfares %}
                    {% if welfare.type == 'oy' %}
                    <div class="card">
                        <div class="title">
                            <span class="emoji">{{welfare.emoji}}</span>
                            {{welfare.title}}
                        </div>
                        <div class="subtitle">{{welfare.subtitle}}</div>
                        <div class="description">
                            <ul>
                                {% for description in welfare.description %}
                                <li class="item">{{description}}</li>
                                {% endfor %}
                            </ul>
                        </div>
                    </div>
                    {% endif %}
                    {% endfor %}   
                </div>  
            </div>
        </div>
    </div>
</div>