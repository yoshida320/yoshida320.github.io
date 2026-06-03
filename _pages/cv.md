---
layout: page
permalink: /cv/
title: cv
nav: true
nav_order: 2
cv_pdf: /assets/rendercv/rendercv_output/Kaito_Yoshida_CV.pdf
---

{% if page.cv_pdf %}

  <div class="cv-page-pdf-link">
    <a
      {% if page.cv_pdf contains '://' %}
        href="{{ page.cv_pdf }}"
      {% else %}
        href="{{ page.cv_pdf | relative_url }}"
      {% endif %}
      target="_blank"
      rel="noopener noreferrer"
      aria-label="Download CV (PDF)"
    >
      <i class="fa-solid fa-file-pdf"></i>
      <span>Download PDF</span>
    </a>
  </div>
{% endif %}

{% assign cv_sections = site.data.cv.cv.sections %}
{% assign cv_page_sections = "education|Education（学歴）|ul,Fellowships and Funding|Fellowships and Funding（採択・支援）|ol,Research Assistantships (RA)|Research Assistantships (RA)|ol,Teaching Assistantships (TA)|Teaching Assistantships (TA)|ol" | split: "," %}

<div class="cv-web">
  {% for section_entry in cv_page_sections %}
    {% assign section_parts = section_entry | split: "|" %}
    {% assign section_key = section_parts[0] %}
    {% assign section_title = section_parts[1] %}
    {% assign list_tag = section_parts[2] %}
    {% assign section_items = cv_sections[section_key] %}

    {% if section_items.size > 0 %}
      <section class="cv-web-section">
        <h2>{{ section_title }}</h2>

      <{{ list_tag }}>
        {% for item in section_items %}
          <li>
            <span class="cv-web-en">
              {%- if item.web_en -%}
                {{ item.web_en }}
              {%- else -%}
                {{ item.number }}
              {%- endif -%}
            </span>
            {% if item.web_ja %}
              <span class="cv-web-ja">{{ item.web_ja }}</span>
            {% endif %}
          </li>
        {% endfor %}
      </{{ list_tag }}>
      </section>
    {% endif %}

{% endfor %}

</div>

<style>
  .cv-page-pdf-link {
    margin-top: 0.5rem;
    margin-bottom: 1.5rem;
  }

  .cv-page-pdf-link a {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.35rem 0.8rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 0.4rem;
    color: var(--global-text-color);
    font-size: 0.95rem;
    text-decoration: none;
  }

  .cv-page-pdf-link a:hover {
    background-color: var(--global-hover-color);
    color: var(--global-theme-color);
  }

  .cv-web-section {
    margin-top: 2rem;
  }

  .cv-web-section:first-child {
    margin-top: 0;
  }

  .cv-web-section ul,
  .cv-web-section ol {
    margin-top: 0.75rem;
    padding-left: 1.5rem;
  }

  .cv-web-section li {
    line-height: 1.5;
    margin-bottom: 0.75rem;
  }

  .cv-web-en,
  .cv-web-ja {
    display: block;
  }

  .cv-web-ja {
    font-size: 0.95rem;
    margin-top: 0.15rem;
    opacity: 0.78;
  }
</style>
