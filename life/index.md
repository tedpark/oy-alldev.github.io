---
layout: main
main: true
title: 소소한 이야기
---

<div class="loading-animation">
<div class="life">
    <div class="pick_line"></div>
    <div class="catalogue">
        {% assign mentions = site.data.mention | sort: 'date' | reverse %}
        {% for mention in mentions %}
            <div class="branch">
                {% include mention.html %}
                {% if mention.comment != null %}
                <div class="comment">
                    {% for mention in mention.comment %}
                    <div class="branch">
                        {% include mention.html %}
                    </div>
                    {% endfor %}
                </div>
                {% endif %}
            </div>
        {% endfor %}
    </div>
</div>
</div>

<script>
    $(document).ready(function () {
        $('.info .date').each(function () {
            let dateString = $(this).text()
                , reggie = /(\d{4})-(\d{2})-(\d{2}) (\d{2}):(\d{2})/
                , [, year, month, day, hours, minutes] = reggie.exec(dateString)
                , dateObject = new Date(year, month - 1, day, hours, minutes);
            $(this).text(timeForToday(dateObject));
            $(this).parent().prop('title', dateString);
        });
    });

    function timeForToday(timeValue) {
        const today = new Date();
        const betweenTime = Math.floor((today.getTime() - timeValue.getTime()) / 1000 / 60);
        if (betweenTime < 1) return '방금전';
        if (betweenTime < 60) {
            return `${betweenTime}분전`;
        }
        const betweenTimeHour = Math.floor(betweenTime / 60);
        if (betweenTimeHour < 24) {
            return `${betweenTimeHour}시간전`;
        }
        const betweenTimeDay = Math.floor(betweenTimeHour / 24);
        if (betweenTimeDay < 31) {
            return `${betweenTimeDay}일전`;
        }
        const betweenTimeMonth = Math.floor(betweenTimeDay / 31);
        if (betweenTimeMonth < 12) {
            return `${betweenTimeMonth}개월전`;
        }
        return `${Math.floor(betweenTimeMonth / 12)}년전`;
    }
</script>