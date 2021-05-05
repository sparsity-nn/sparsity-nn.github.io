---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
---

<div>
{% for conference_name in site.data.conference_list %}
    <div class="conference_title">
        {{ conference_name.title }}
        <hr>
    </div>
    <div>
        {% for row in site.data[conference_name.tag] %}
            <div class="paper_row">
                <div class="paper_header">
                    <div class="paper_title">
                        <a href="{{ row.paper_url }}" target="_blank">{{ row.title }}</a>
                    </div>
                    <div class="paper_year">({{ row.year }})</div>
                </div>
                <div class="paper_author">
                    <i>{{ row.author }}</i>
                </div>
                <div class="paper_absact">
                    {{ row.abstract }}
                </div>
            </div>
        {% endfor %}
    </div>
{% endfor %}
</div>

<!-- <div>
{% for conference_name in site.data.conference_list %}
    <h1> {{ conference_name.title }} </h1>
    <table>
        <tr>
            <th>Title</th>
            <th>Authors</th>
            <th>Year</th>
        </tr>
        <tr>
            {% for row in site.data[conference_name.tag] %}
                <td><a href="{{ row.paper_url }}" target="_blank">{{ row.title }}</a></td>
                <td>{{ row.author }}</td>
                <td>{{ row.year }}</td>
            {% endfor %}
        </tr>
    </table>
{% endfor %}
</div> -->

<style type="text/css">
    .conference_title {
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

    .paper_header {
        margin: 0;
    }

    .paper_title {
        float: left;
        width: 90%;
        margin: 0;
    }

    .paper_title a {
        font-size: 1.25em;
        color: blue;
    }

    .paper_year {
        font-size: 1.25em;
        float: right;
        width: 10%;
        margin: 0;
    }

    .paper_author {
        color: grey;
        margin: 0;
    }

    .paper_absact {
        text-align: justify
    }
</style>
