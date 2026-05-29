---
permalink: /members/
title: "Members"
---

{% for author in site.data.authors %}
{% assign member = author[1] %}
{% if member.member and member.current %}

## {{ member.name }}

{% if member.avatar %}
![Photograph of {{member.name}}]({{member.avatar}}){:style="float: left; object-fit: contain; width: 30%; max-height: 12em; margin-right: 1.5em; margin-bottom: 1em;"}
{% endif %}

{% if member.bio %}
**{{ member.bio }}**
{% endif %}

{% if member.email %}
Email: [{{ member.email }}](mailto:{{ member.email }})
{% endif %}

{% if member.website %}
[Personal website]({{ member.website }})
{% endif %}

{% if member.twitter %}
[@{{ member.twitter }}](https://twitter.com/{{ member.twitter }})
{% endif %}

{% if member.bluesky %}
[@{{ member.bluesky }}](https://bsky.app/profile/{{ member.bluesky }})
{% endif %}

{{ member.fullbio }}

<div style="clear: both; margin-bottom: 4em;"></div>

{% endif %}
{% endfor %}

# Former members

{% for author in site.data.authors %}
{% assign member = author[1] %}
{% if member.member %}
{% unless member.current %}

### {{ member.name }}

{% if member.bio %}
**{{ member.bio }}** {% if member.start %}({{ member.start }}{% if member.end and member.start != member.end %}&ndash;{{ member.end }}{% endif %}){% endif %}
{% endif %}

{% if member.next %}
Next position: {{ member.next }}
{% endif %}

{% endunless %}
{% endif %}
{% endfor %}

<hr style="margin-top: 4em;">

# Joining

If you are interested in joining, please contact [Dr. Greene](https://www.egreenelab.org/members/#eric-greene) by email to set up an appointment. Please note, that San Francisco State University does NOT have a Ph.D. granting program in the chemical or biological sciences---if you are looking for a Ph.D. position please inquire at other universities.
