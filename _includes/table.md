{%- if include.year=='' -%}
{%- assign selection=site.data.positions | where: "status", include.status -%}
{%- else -%}
{%- assign selection=site.data.positions | where: "status", include.status | where: "year", include.year -%}
{%- endif %}


<style>
    {
        box-sizing: border-box;
    }
    /* Set additional styling options for the columns*/
    .column {
    float: left;
    width: 50%;
    }

    .row:after {
    content: "";
    display: table;
    clear: both;
    }
</style>


{%- for pos in selection -%}
---
<h2><a href="{{ pos.url }}" target="_blank">{{ pos.name }}</a></h2>

{{ pos.descr }}
{{ pos.deadl }}


<div class="row">
        <div class="column">
            Short list:
            {% for item in pos.slist %}
            <p> {{ item }}</p>
            {% endfor %}
        </div>
        <div class="column">
            Offer list:
            {% for item in pos.olist %}
            <p> {{ item }}</p>
            {% endfor %}
        </div>
</div>
{%- endfor -%}
