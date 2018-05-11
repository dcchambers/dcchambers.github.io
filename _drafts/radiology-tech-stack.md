---
title: Radiology Tech Stack
---

In January of 2018 I started a new job with the Department of Radiology in
the University of Wisconsin's School of Medicine and Public Health. Phew, that
was a mouthful. From here on out, I'll just refer to it as "Radiology."

Our department is dual-purpose. We support both academic research in the
School of Medicine and we build and support clinical applications that are
used every day by doctors and staff in the UW Hospital and Clinics.
We're a pretty small team. Our core team is just five people -
four developers and me, the dev/ops engineer guy. We also work closely
with our media team for graphics work, content updates, and some
design/front-end work. We also work with the Server Team at UW Health for our
infrastructure needs.

So, what does the tech stack for a unique group like ours? I could just go ahead
and list a bunch of tools without explaining *how* we use them - but my guess is
you're here to see *how and why* we use certain tools. It's easy enough to head
to a website like [stackshare](https://stackshare.io) and have a bunch of
technologies thrown at you without any indication of how they're used. Instead,
I think it will be more fun to explore how we use different technologies.

## What We Do

So what does a development team in a Radiology department do? Radiology is a
medical specialty that uses medical imaging to diagnose and help treat issues
within the body.

Medical imaging covers everything from X-Rays to MRI (Magnetic Resonance
Imaging) to CT (Computed Tomography) to PET (Positron Emission Tomography)
scans to Ultrasound. Radiology is involved in pretty much every aspect of
healthcare. Break a bone? A radiologist will read the X-ray. Have a traumatic
brain injury or stroke? A radiologist will read the CT scan or look for an
aneurysm. Searching for cancer cells? A radiologist will help with that too.

Radiology has long been a pioneer of technological advances in healthcare, and
a lot of the focus is on improving these technologies through various means. We
work closely with the informatics group to analyze large data sets. We work with
medical physics to improve scanners and develop new technologies to see inside
the body.

As a development team, a lot of our work is improving the workflow and
efficiency of Radiologists and other staff members. We work directly with
stakeholders within the department, most of them medical doctors, to create
tools that will help them in the field. Because we work at a teaching hospital,
we also develop tools to help foster communication and learning between med
students, residents, and attending physicians.


## Legacy applications

Most of our existing legacy applications are regular good 'ol LAMP stack
applications. The (L)inux (A)pache (M)ysql (P)HP stack is battle-tested for
sure.

## New applications

Ultimately, the nature of our department means we get a very wide range of
requests. Some 'application' requests are simple web-pages that have a dashboard
that displays data in some database. Other requests are more involved - like a
mobile app for calculating gadolinium dosages or an application that allows
Residents to compare their radiology reading room preliminary examinations to
an attending physician's final exam.

## Infrastructure

## Development Environments



##  List of everything
* Programming
  * PHP (legacy, maintenance, and wordpress site)
  * HTML/CSS, JS (frontend)
  * iOS - Swift
  * Android - Java?
  * Ruby on Rails --> Philips/AI Bridge Platform
    * Ruby (jRuby)
    * Postgresql
    * Bundler
  * Java (legacy only - no new development)
  * Groovy/Grails (legacy only - no new dev)
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
