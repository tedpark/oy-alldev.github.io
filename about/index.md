---
layout: main
main: true
title: 개발팀 소개
---

<div class="loading-animation">
    <div class="about">
        우리는 올리브영 디벨로퍼즈, 올디브입니다!<br/>
        올리브영의 모든 것을 개발한다는 뜻인 'All dev'의 의미를 담고 있어요.<br/>

        <div class="title">개발 문화</div>
        <div class="content">
            <div class="subtitle">우리는 다음과 같은 문화를 갖거나 추구하고 있습니다.</div>
            <ul class="culture">
                <li>모든 코드는 리뷰를 거칩니다.</li>
                <li>용어 선정에 심혈을 기울입니다.</li>
                <li>작업에 앞서 설계 단계를 거칩니다. 다만 설계를 위한 설계는 하지 않습니다.</li>
                <li>주석은 최소한으로 유지합니다.</li>
                <li>잘못된 주석은 오히려 유지 비용을 증가시킨다고 생각합니다. 가급적 코드로 표현하려고 합니다.</li>
                <li>스페셜리스트보다는 제너럴리스트</li>
                <li>야근은 가급적 하지 않습니다.</li>
                <li>관여하지 않는 프로젝트의 진행도 모두 알 수 있도록 주기적으로 공유합니다.</li>
                <li>책 구입을 권장합니다.</li>
                <li>지속적 통합 / 지속적 배포 / 데브옵스를 추구합니다.</li>
            </ul>
        </div>
    
        <div class="title">개발 환경</div>
        <div class="content">
            <div class="subtitle">우리는 다음과 같은 환경에서 개발하고 있습니다.</div>
            <ul class="environment">
                <li>소스는 내부 GitLab 저장소를 사용해 관리하고 있습니다.</li>
                <li>타팀과의 업무는 레드마인을 통해 관리/진행합니다.</li>
                <li>개발팀 내부에서는 GitLab 이슈를 통해 업무에 대한 작업 내역을 관리합니다.</li>
                <li>회사 내 커뮤니케이션은 Slack을 사용합니다.</li>
                <li>문서는 위키를 사용해 작성합니다.</li>
            </ul>
        </div>

        <div class="title">개발자 소개</div>
        <div class="content">
            <ul>
                {% for member in site.data.members %}
                    <li class="member_card">
                        <div class="thumbnail">
                            {{% if member.thumbnail != nil %}}
                            <img class="profile" src="/meta/members/{{ member.thumbnail }}" />
                            {{% endif %}}
                            <div class="emoji">
                                <span>{{member.emoji}}</span>
                            </div>
                        </div>
                        <div class="info">
                            <div class="name">{{member.name}}</div>
                            <div class="description">{{member.comment}}</div>
                        </div>
                    </li>
                {% endfor %}
            </ul>
        </div>
    </div>
</div>