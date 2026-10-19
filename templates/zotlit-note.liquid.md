## Title and Authors of the Paper

- "{{ zt.title }}"
- {{ zt.authors | map: "fullName" | join: ", " }}
- {% if zt.containerTitle %}*{{ zt.containerTitle }}*{% endif %}{% if zt.volume %} {{ zt.volume }}{% endif %}{% if zt.issue %}({{ zt.issue }}){% endif %}{% if zt.pages %}: {{ zt.pages }}{% endif %} ({{ zt.date | append: "" | slice: 0, 4 }}){% if zt.DOI %}; doi: {{ zt.DOI }}{% endif %}
- [Zotero]({{ zt.backlink }}) {{ zt.attachments | map: "fileLink" | compact | join: " " }}

{% bq %}
[!question] Abstract
{{ zt.abstract | default: "No abstract available." }}
{% endbq %}

## Citeable insights (red)

{% for annot in zt.annotations %}{% if annot.colorName == "red" %}
{% bq %}
[!important] Page {{ annot.pageLabel }}

{% if annot.comment %}{{ annot.comment }}

{% endif %}{% bq %}
[!quote]- Quote
{{ annot.imgLink | embed }}{{ annot.text }}
{% endbq %}
{% endbq %}
{% endif %}{% endfor %}

## Open questions (green)

{% for annot in zt.annotations %}{% if annot.colorName == "green" %}
{% bq %}
[!question] Page {{ annot.pageLabel }}

{% if annot.comment %}{{ annot.comment }}

{% endif %}{% bq %}
[!quote]- Quote
{{ annot.imgLink | embed }}{{ annot.text }}
{% endbq %}
{% endbq %}
{% endif %}{% endfor %}

## General notes (yellow)

{% for annot in zt.annotations %}{% if annot.colorName == "yellow" %}
{% bq %}
[!note] Page {{ annot.pageLabel }}

{% if annot.comment %}{{ annot.comment }}

{% endif %}{% bq %}
[!quote]- Quote
{{ annot.imgLink | embed }}{{ annot.text }}
{% endbq %}
{% endbq %}
{% endif %}{% endfor %}

## Other annotations

{% for annot in zt.annotations %}{% unless annot.colorName == "red" or annot.colorName == "green" or annot.colorName == "yellow" %}
{% bq %}
[!quote] Page {{ annot.pageLabel }} ({{ annot.colorName | default: "no color" }})

{% if annot.comment %}{{ annot.comment }}

{% endif %}{% bq %}
[!quote]- Quote
{{ annot.imgLink | embed }}{{ annot.text }}
{% endbq %}
{% endbq %}
{% endunless %}{% endfor %}
