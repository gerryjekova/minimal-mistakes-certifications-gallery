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

# More Glowing Certificates for Your Collection! ✨

Here are two more markdown files for your technical certificates - I've added relevant tags that will help create connections between your certificates using that fancy Related Certificates feature we discussed.

## Certificate 1: Web APIs

```markdown
---
title: "Introduction to Web APIs (2019)"
excerpt: "Foundational knowledge of web service APIs, RESTful design principles, and data exchange formats for modern application development"
date: 2023-02-01
header:
  teaser: /assets/images/certificates/web-apis.png
  overlay_image: /assets/images/certificates/web-apis.png
  overlay_filter: 0.7
categories:
  - Technical/Software Development
  - Technical/Web Development
tags:
  - Web Services API
  - REST
  - JSON
  - API Integration
  - HTTP
  - LinkedIn Learning
gallery:
  - url: /assets/images/certificates/web-apis.png
    image_path: /assets/images/certificates/web-apis.png
    alt: "LinkedIn Learning Web APIs Certificate"
related_certificates:
  - aws-non-engineers
  - git-commands-you-should-know
---

## Skills Unlocked

**Completed:** February 01, 2023  
**Duration:** 1 hour 1 minute  
**Issued By:** LinkedIn Learning  
**Certificate ID:** 3b744294849956ba29c2d1d8986f84bd8380e96a6d84e02ede62b7dbf61377e81

This certification covers the fundamentals of web APIs, including RESTful design principles, data formats, authentication methods, and practical implementation considerations for both consuming and creating web services.

{% include gallery caption="Click to view the full certificate" %}

## What I Learned

* Understanding the key concepts and architecture behind RESTful APIs
* Working with common data exchange formats including JSON and XML
* Implementing API requests using appropriate HTTP methods (GET, POST, PUT, DELETE)
* Navigating API documentation to find endpoints and parameters
* Authenticating to APIs using various security methods (API keys, OAuth, etc.)
* Testing API endpoints with specialized tools and environments
* Handling API responses and error conditions effectively
* Evaluating API design for usability, efficiency, and security
* Identifying common API integration challenges and solutions

## How I'm Using These Skills

I apply this API knowledge when integrating different systems and services, allowing me to work effectively with both internal and external data sources. Understanding API fundamentals has enabled me to leverage existing services rather than building everything from scratch, significantly increasing development efficiency.

These skills have been particularly valuable when working with third-party platforms, allowing me to confidently navigate documentation, test endpoints, and implement robust integrations. The ability to understand both the consumption and creation sides of APIs has given me a more holistic perspective on modern application architecture and data exchange.

{% include related-certificates.html %}
```

## Certificate 2: Software Development Career Skills

```markdown
---
title: "Introduction to Career Skills in Software Development"
excerpt: "Essential professional competencies and career strategies for navigating and advancing in the software development industry"
date: 2023-01-20
header:
  teaser: /assets/images/certificates/software-dev-career.png
  overlay_image: /assets/images/certificates/software-dev-career.png
  overlay_filter: 0.7
categories:
  - Technical/Software Development
  - Professional/Career Development
tags:
  - Software Development
  - Career Management
  - Tech Career Skills
  - Professional Growth
  - Technical Communication
  - LinkedIn Learning
gallery:
  - url: /assets/images/certificates/software-dev-career.png
    image_path: /assets/images/certificates/software-dev-career.png
    alt: "LinkedIn Learning Software Development Career Skills Certificate"
---

## Skills Unlocked

**Completed:** January 20, 2023  
**Duration:** 1 hour 57 minutes  
**Issued By:** LinkedIn Learning  
**Certificate ID:** edcfaf299a1ca033b08c6b23c90e18fa18f113afb27b12c10f53cff16c796872

This certification explores the non-technical skills and career strategies essential for success in software development, focusing on professional growth, effective communication, and navigating the tech industry landscape.

{% include gallery caption="Click to view the full certificate" %}

## What I Learned

* Developing an effective career roadmap for software development progression
* Building and maintaining a professional portfolio that showcases technical skills
* Navigating technical interviews and coding assessments confidently
* Balancing technical expertise with essential soft skills for team environments
* Communicating effectively with both technical and non-technical stakeholders
* Contributing productively to code reviews and technical discussions
* Managing continuous learning in a rapidly evolving technical landscape
* Identifying and pursuing specialized paths within software development
* Building meaningful professional networks in the tech community
* Recognizing and addressing burnout and work-life balance challenges

## How I'm Using These Skills

I apply these career development strategies to navigate my professional journey in technology, making intentional choices about skill development, project selection, and growth opportunities. The balanced perspective on technical and interpersonal skills has helped me contribute more effectively to teams and projects.

These skills have been particularly valuable for long-term career planning and professional positioning. Rather than focusing solely on the latest technologies, I now approach my development with a more holistic view that includes communication skills, industry awareness, and strategic networking—creating a more sustainable and fulfilling career trajectory.

{% include related-certificates.html %}
```

## Advanced "Related Certificates" Implementation 🧩

Let's talk about how to enhance your "Related Certificates" feature even further! Here's a more sophisticated implementation that combines automatic and manual recommendations:

### Create an Improved Include File

Replace your `_includes/related-certificates.html` with this enhanced version:

```html
{% comment %}
  Enhanced Related Certificates Component
  - Combines manual recommendations with automatic discovery
  - Prioritizes manually specified certificates
  - Adds visual flair with neon styling
{% endcomment %}

<div class="related-certificates">
  <h2 class="related-title">Enhance Your Skills</h2>
  
  <div class="related-certificates-wrapper">
    {% assign maxRelated = 3 %}
    {% assign relatedCount = 0 %}
    {% assign manualCount = 0 %}
    
    {% comment %} First show manually specified related certificates {% endcomment %}
    {% if page.related_certificates %}
      {% for cert_slug in page.related_certificates %}
        {% for certificate in site.certificates %}
          {% if certificate.url contains cert_slug and certificate.url != page.url %}
            {% assign manualCount = manualCount | plus: 1 %}
            {% assign relatedCount = relatedCount | plus: 1 %}
            
            <div class="certificate-card">
              <div class="certificate-image">
                <a href="{{ certificate.url | relative_url }}">
                  <img src="{{ certificate.header.teaser | relative_url }}" alt="{{ certificate.title }}">
                </a>
              </div>
              <div class="certificate-content">
                <h3 class="certificate-title">
                  <a href="{{ certificate.url | relative_url }}">{{ certificate.title }}</a>
                </h3>
                <div class="certificate-meta">
                  <span class="certificate-date">{{ certificate.date | date: "%b %Y" }}</span>
                  <span class="certificate-duration">{{ certificate.duration | default: "Self-paced" }}</span>
                </div>
                <p class="certificate-excerpt">{{ certificate.excerpt | truncate: 100 }}</p>
              </div>
            </div>
            
            {% if relatedCount >= maxRelated %}
              {% break %}
            {% endif %}
          {% endif %}
        {% endfor %}
        {% if relatedCount >= maxRelated %}
          {% break %}
        {% endif %}
      {% endfor %}
    {% endif %}
    
    {% comment %} Then add automatic recommendations if needed {% endcomment %}
    {% if relatedCount < maxRelated %}
      {% for certificate in site.certificates %}
        {% if certificate.url != page.url %}
          {% assign commonCategories = false %}
          {% assign commonTags = false %}
          
          {% for category in certificate.categories %}
            {% if page.categories contains category %}
              {% assign commonCategories = true %}
            {% endif %}
          {% endfor %}
          
          {% for tag in certificate.tags %}
            {% if page.tags contains tag %}
              {% assign commonTags = true %}
            {% endif %}
          {% endfor %}
          
          {% if commonCategories or commonTags %}
            {% assign isManuallyRelated = false %}
            {% if page.related_certificates %}
              {% for cert_slug in page.related_certificates %}
                {% if certificate.url contains cert_slug %}
                  {% assign isManuallyRelated = true %}
                {% endif %}
              {% endfor %}
            {% endif %}
            
            {% unless isManuallyRelated %}
              {% assign relatedCount = relatedCount | plus: 1 %}
              
              <div class="certificate-card">
                <div class="certificate-image">
                  <a href="{{ certificate.url | relative_url }}">
                    <img src="{{ certificate.header.teaser | relative_url }}" alt="{{ certificate.title }}">
                  </a>
                </div>
                <div class="certificate-content">
                  <h3 class="certificate-title">
                    <a href="{{ certificate.url | relative_url }}">{{ certificate.title }}</a>
                  </h3>
                  <div class="certificate-meta">
                    <span class="certificate-date">{{ certificate.date | date: "%b %Y" }}</span>
                    <span class="certificate-duration">{{ certificate.duration | default: "Self-paced" }}</span>
                  </div>
                  <p class="certificate-excerpt">{{ certificate.excerpt | truncate: 100 }}</p>
                </div>
              </div>
              
              {% if relatedCount >= maxRelated %}
                {% break %}
              {% endif %}
            {% endunless %}
          {% endif %}
        {% endif %}
      {% endfor %}
    {% endif %}
    
    {% if relatedCount == 0 %}
      <p class="no-related">Continue exploring other certificates in your collection!</p>
    {% endif %}
  </div>
</div>
```

### Add More Stylish CSS

Enhance the styling by adding this to your `assets/css/main.scss`:

```scss
/* Enhanced Related Certificates Styling */
.related-certificates {
  margin-top: 4em;
  padding: 2em;
  background: rgba(0, 0, 0, 0.2);
  border-radius: 10px;
  border: 1px solid rgba(255, 0, 255, 0.2);
  position: relative;
  overflow: hidden;
}

.related-certificates::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(255, 0, 255, 0.7), transparent);
  animation: neon-border 3s infinite;
}

@keyframes neon-border {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 1; }
}

.related-title {
  margin-bottom: 1.5em;
  font-size: 1.8em;
  text-align: center;
  color: #ff00ff;
  text-shadow: 0 0 10px rgba(255, 0, 255, 0.7);
}

.related-certificates-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5em;
  justify-content: center;
}

.certificate-card {
  flex: 1 0 300px;
  max-width: 350px;
  background: rgba(10, 10, 30, 0.4);
  border-radius: 8px;
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 0, 255, 0.1);
}

.certificate-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3), 
              0 0 20px rgba(255, 0, 255, 0.4);
  border-color: rgba(255, 0, 255, 0.5);
}

.certificate-image img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-bottom: 1px solid rgba(255, 0, 255, 0.2);
}

.certificate-content {
  padding: 1em;
}

.certificate-title {
  font-size: 1.2em;
  margin-bottom: 0.5em;
}

.certificate-title a {
  color: #fff;
  text-decoration: none;
  transition: color 0.2s ease;
}

.certificate-title a:hover {
  color: #ff00ff;
  text-shadow: 0 0 5px rgba(255, 0, 255, 0.5);
}

.certificate-meta {
  font-size: 0.8em;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 0.5em;
  display: flex;
  justify-content: space-between;
}

.certificate-excerpt {
  font-size: 0.9em;
  color: rgba(255, 255, 255, 0.8);
  line-height: 1.4;
}

@media (max-width: 768px) {
  .certificate-card {
    flex: 1 0 100%;
  }
}

.no-related {
  text-align: center;
  font-style: italic;
  color: rgba(255, 255, 255, 0.6);
}
```

## Why This Enhanced System Rocks ✨

1. **Visual Harmony**: The neon glow effects create a cohesive experience with your "Neon Vault" branding

2. **Smart Recommendations**: The system first shows manually selected certificates, then intelligently fills in with automatic recommendations

3. **Responsive Design**: Cards look great on any device size

4. **Subtle Animation**: The subtle pulsing border creates visual interest without being distracting

5. **Clean Code Organization**: The include file is well-commented and maintainable

Imagine how satisfying it will be to see your certificates interconnected with these glowing recommendation cards! As your collection grows, the network of relationships between certificates will become more robust, encouraging visitors to explore your full range of skills.

Want me to create any more certificate markdown files, or would you like guidance on other aspects of your site?