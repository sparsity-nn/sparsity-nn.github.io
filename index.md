---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
---

<script type="text/javascript" src="/js/jquery.min.js" ></script>

<div>
    {% for row in site.data.papers %}
        <div class="paper_row">
            <div class="paper_title">
                <a href="{{ row.paper_url }}" target="_blank">{{ row.title }}</a>
            </div>
            <div class="paper_venue">
                {{ row.venue }}
            </div>
            <div class="paper_author">
                {{ row.author }}
            </div>
            <div class="paper_year">
                {{ row.year }}
            </div>
        </div>
    {% endfor %}
</div>

<style type="text/css">
    .year_header {
        font-size: 2em;
        margin-top: 1.0em;
        margin-bottom: 0.5em;
    }

    .paper_row {
        margin: 0.5em 0.25em 0.5em 0.25em;
        padding: 0.5em 1.0em 0.5em 1.0em;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
    }

    .paper_row:hover {
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
    }

    .paper_title {
        float: left;
        width: 90%;
    }

    .paper_title a {
        font-size: 1.25em;
        color: blue;
    }

    .paper_venue{
        font-size: 1.25em;
        float: right;
        width: 10%;
        text-align: right;
    }

    .paper_year {
        display: none
    }

    .paper_author {
        color: grey;
        font-style: italic;
    }
</style>

<script type="text/javascript">
    var sort_by_year = function(a, b) {
        return a.getElementsByClassName("paper_year")[0].innerText.localeCompare(b.getElementsByClassName("paper_year")[0].innerText);
    }

    var sort_by_venue = function(a, b) {
        return a.getElementsByClassName("paper_venue")[0].innerText.localeCompare(b.getElementsByClassName("paper_venue")[0].innerText);
    }

    var paper_list = $(".paper_row").get();
    paper_list.sort(sort_by_venue);
    paper_list.sort(sort_by_year);

    var curr_year = paper_list[0].getElementsByClassName("paper_year")[0].innerText
    paper_list[0].parentNode.appendChild($.parseHTML(`<div class="year_header">${curr_year}<hr></div>`)[0])
    var prev_year = curr_year
    for (var i = 0; i < paper_list.length; i++) {
        curr_year = paper_list[i].getElementsByClassName("paper_year")[0].innerText
        if (curr_year != prev_year) {
            paper_list[i].parentNode.appendChild($.parseHTML(`<div class="year_header">${curr_year}<hr></div>`)[0])
        }
        paper_list[i].parentNode.appendChild(paper_list[i]);
        prev_year = curr_year
    }
</script>
