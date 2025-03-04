# Two More Certificates for Your Neon Vault! ✨

Let me craft those markdown files for you and show you how to implement a cool "Related Certificates" feature that will tie your collection together beautifully.

## Certificate 1: AWS for Non-Engineers

```markdown
---
title: "Introduction to AWS for Non-Engineers: 3 Core Services"
excerpt: "Essential overview of key AWS services designed for professionals who need cloud fundamentals without engineering complexity"
date: 2023-01-25
header:
  teaser: /assets/images/certificates/aws-non-engineers.png
  overlay_image: /assets/images/certificates/aws-non-engineers.png
  overlay_filter: 0.7
categories:
  - Technical/Cloud
  - Technical/AWS
tags:
  - AWS
  - Cloud Computing
  - S3
  - EC2
  - RDS
  - LinkedIn Learning
gallery:
  - url: /assets/images/certificates/aws-non-engineers.png
    image_path: /assets/images/certificates/aws-non-engineers.png
    alt: "LinkedIn Learning AWS for Non-Engineers Certificate"
---

## Skills Unlocked

**Completed:** January 25, 2023  
**Duration:** 1 hour 19 minutes  
**Issued By:** LinkedIn Learning  
**Certificate ID:** AddMSEdM_SdLXqXnU7Ik0gA1fw2

This certification provides a non-technical introduction to Amazon Web Services' core infrastructure services, focusing on practical understanding and use cases rather than implementation details.

{% include gallery caption="Click to view the full certificate" %}

## What I Learned

* Understanding the fundamental concepts of cloud computing and AWS architecture
* Navigating the AWS Management Console with confidence
* Creating and managing S3 buckets for secure and scalable storage solutions
* Setting up basic EC2 instances and understanding their role in cloud infrastructure
* Working with RDS databases without advanced database administration knowledge
* Implementing basic security best practices for AWS resources
* Estimating costs and optimizing AWS spending for business needs
* Identifying when and how to leverage these core services for business applications
* Communicating effectively with technical teams about AWS implementations

## How I'm Using These Skills

I apply this AWS knowledge to better collaborate with technical teams and make informed decisions about cloud solutions. By understanding the capabilities and constraints of core AWS services, I can contribute more effectively to discussions about infrastructure needs and possibilities.

These skills have been particularly valuable when working at the intersection of business and technology, allowing me to translate between technical concepts and business requirements. The ability to understand cloud fundamentals has empowered me to propose solutions that leverage AWS capabilities appropriately without requiring deep technical expertise.

{% include related-certificates.html %}
```

## Certificate 2: Impromptu Speaking

```markdown
---
title: "Impromptu Speaking"
excerpt: "Techniques for delivering clear, confident, and structured responses with minimal preparation in professional settings"
date: 2025-02-27
header:
  teaser: /assets/images/certificates/impromptu-speaking.png
  overlay_image: /assets/images/certificates/impromptu-speaking.png
  overlay_filter: 0.7
categories:
  - Professional/Communication
  - Professional/Presentation Skills
tags:
  - Extemporaneous Speaking
  - Public Speaking
  - Communication Skills
  - Professional Development
  - LinkedIn Learning
gallery:
  - url: /assets/images/certificates/impromptu-speaking.png
    image_path: /assets/images/certificates/impromptu-speaking.png
    alt: "LinkedIn Learning Impromptu Speaking Certificate"
related_certificates:
  - how-to-speak-so-people-want-to-listen
  - how-to-present-and-stay-on-point
---

## Skills Unlocked

**Completed:** February 27, 2025  
**Duration:** 22 minutes  
**Issued By:** LinkedIn Learning  
**Certificate ID:** cbf756200f465b8e073414c51ab8c6a6489c3eb7c2de619f00a2a0914e99cf29f

This certification covers techniques for thinking on your feet and delivering organized, coherent responses with little to no preparation time, a crucial skill for meetings, Q&A sessions, and unexpected speaking opportunities.

{% include gallery caption="Click to view the full certificate" %}

## What I Learned

* Implementing frameworks for structuring impromptu responses clearly and logically
* Managing anxiety and building confidence when speaking without preparation
* Using the PREP method (Point, Reason, Example, Point) for organized responses
* Leveraging personal experiences and knowledge to illustrate key points effectively
* Employing bridging techniques to handle difficult or unexpected questions
* Practicing active listening to respond directly to what's being asked
* Developing concise responses that avoid rambling or going off-topic
* Building a mental library of examples and stories for various speaking scenarios
* Using appropriate body language and vocal delivery under pressure

## How I'm Using These Skills

I apply these impromptu speaking techniques in various professional contexts, from team meetings and client interactions to networking events where unexpected questions arise. The structured approach to organizing thoughts quickly has increased my confidence in high-pressure communication situations.

These skills have been particularly valuable in leadership roles where I'm often called upon to provide insights or make decisions on the spot. By implementing effective frameworks for impromptu responses, I've been able to deliver more thoughtful, clear, and impactful communications even without preparation time.

{% include related-certificates.html %}
```

## Now, Let's Add a "Related Certificates" Feature! 🔄

Here's how to implement a feature that will automatically show related certificates based on categories and tags:

### Step 1: Create the Include File

First, create a new file at `_includes/related-certificates.html` with this content:

```html
{% comment %}
  Show related certificates based on categories and tags
{% endcomment %}

<div class="related-certificates">
  <h2 class="related-title">Related Certificates</h2>
  
  <div class="grid__wrapper">
    {% assign maxRelated = 3 %}
    {% assign minCommonTags = 1 %}
    {% assign maxRelatedCounter = 0 %}
    
    {% for certificate in site.certificates %}
      {% assign sameTagCount = 0 %}
      {% assign commonTags = '' %}
      
      {% for tag in certificate.tags %}
        {% if certificate.url != page.url %}
          {% if page.tags contains tag %}
            {% assign sameTagCount = sameTagCount | plus: 1 %}
            {% capture tagmarkup %} <span class="label label-default">{{ tag }}</span> {% endcapture %}
            {% assign commonTags = commonTags | append: tagmarkup %}
          {% endif %}
        {% endif %}
      {% endfor %}
      
      {% if sameTagCount >= minCommonTags and certificate.url != page.url %}
        {% if maxRelatedCounter < maxRelated %}
          <div class="grid__item">
            <article class="archive__item">
              <div class="archive__item-teaser">
                <img src="{{ certificate.header.teaser | relative_url }}" alt="{{ certificate.title }}">
              </div>
              <h3 class="archive__item-title">
                <a href="{{ certificate.url | relative_url }}" rel="permalink">{{ certificate.title }}</a>
              </h3>
              <p class="archive__item-excerpt">{{ certificate.excerpt | markdownify | strip_html | truncate: 160 }}</p>
            </article>
          </div>
          {% assign maxRelatedCounter = maxRelatedCounter | plus: 1 %}
        {% endif %}
      {% endif %}
    {% endfor %}
    
    {% if maxRelatedCounter == 0 %}
      <p>No related certificates found at this time.</p>
    {% endif %}
  </div>
</div>
```

### Step 2: Add Some Styling

Add this to your `assets/css/main.scss` file (or create it if it doesn't exist):

```scss
---
---

@import "{{ site.theme }}";

/* Related Certificates Styling */
.related-certificates {
  margin-top: 3em;
  padding-top: 1.5em;
  border-top: 3px solid rgba(255, 0, 255, 0.3);
}

.related-title {
  margin-bottom: 1em;
  font-size: 1.5em;
  color: #ff00ff;
  text-shadow: 0 0 10px rgba(255, 0, 255, 0.5);
}

.related-certificates .grid__wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5em;
}

.related-certificates .grid__item {
  flex: 1 0 300px;
  max-width: 350px;
  transition: all 0.3s ease;
}

.related-certificates .grid__item:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3), 
              0 0 20px rgba(255, 0, 255, 0.3);
}

.related-certificates .archive__item-teaser img {
  border-radius: 8px;
  border: 1px solid rgba(255, 0, 255, 0.3);
}
```

### Step 3: Implement in Your Certificate Files

You've already seen I added this line in both certificate templates:

```markdown
{% include related-certificates.html %}
```

Just add that line at the end of all your certificate markdown files.

### Step 4 (Optional): Manual Related Certificates

If you want more control, you can manually specify related certificates like I did in the Impromptu Speaking example:

```yaml
related_certificates:
  - how-to-speak-so-people-want-to-listen
  - how-to-present-and-stay-on-point
```

Then modify the include file to use these if available:

```html
{% if page.related_certificates %}
  <div class="grid__wrapper">
    {% for cert_name in page.related_certificates %}
      {% assign certificate = site.certificates | where: "slug", cert_name | first %}
      {% if certificate %}
        <!-- Display certificate here (same code as above) -->
      {% endif %}
    {% endfor %}
  </div>
{% else %}
  <!-- Automatic related certificates logic -->
{% endif %}
```

## The Magic Behind This Feature 🪄

What makes this feature awesome:

1. **Automatic discovery**: It finds related certificates based on shared tags without you having to manually link them

2. **Visual consistency**: The neon styling fits perfectly with your site's theme

3. **Encourages exploration**: Visitors will naturally click through to explore more of your certificates

4. **SEO boost**: Internal linking between related content helps search engines understand your site structure

5. **Flexible implementation**: Use automatic discovery or manually specify exactly which certificates to show

Would you like me to refine any part of this? Or shall we create markdown files for a few more of your certificates?