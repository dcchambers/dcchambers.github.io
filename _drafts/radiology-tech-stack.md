---
title: Radiology Tech Stack
---

In January of 2018 I started a new job with the Department of Radiology in
the University of Wisconsin's School of Medicine and Public Health. Phew, that
was a mouthful. From here on out, I'll just refer to it as "Radiology."

Our department is dual-purpose. We support both academic research in the
School of Medicine, and we support clinical applications that are used every
day by doctors and staff in the UW Hospital and Clinics. We're a pretty small
team. Our core team is just five people - four developers and me, the dev/ops
engineer guy. We also work closely with our media team for graphics work
and some design/front-end work, and we work with the Server Team at UW Health
for our infrastructure needs.

So, what's in the tech stack for a unique group like ours? I could just go ahead
and list a bunch of tools without explaining *how* we use them - but my guess is
you're here to see *how and why* we use certain tools. It's easy enough to head
to a website like [stackshare](https://stackshare.io) and have a bunch of
technologies thrown at you without any indication of how they're used. Instead,
I think it will be more fun to explore how we use different technologies.

## What We Do

So what does a development team in a Radiology department do? Radiology is a
medical specialty that uses medical imaging to diagnose issues within the body.
Medical imaging covers everything from X-Rays to MRI (Magnetic Resonance
Imaging) to CT (Computed Tomography) to PET (Positron Emission Tomography)
scans to Ultrasound.



##############################
### Operating System

While most good applications these days are OS-agnostic, it's still an
important cog in the dev/ops machine. We run all our our webapps on Linux
servers.

### Legacy applications

Most of our existing legacy applications are regular good 'ol LAMP stack
applications. The (L)inux (A)pache (M)ysql (P)HP stack is battle-tested for
sure.


## List of everything
* Programming
  * PHP (legacy, maintenance, and wordpress site)
  * HTML/CSS, JS (frontend)
  * iOS - Swift
  * Android - Java?
  * Ruby on Rails
  * Java (legacy only - no new development)
  *
* Dev/Ops
  * Docker
  * Jenkins
  * Nginx (Reverse Proxy)
  * Apache
* Misc.
  * Linux
    * Ubuntu 16.04 LTS
    * RHEL7/CentOS7
  * MySQL
  
