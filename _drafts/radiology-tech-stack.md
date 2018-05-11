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
aneurysm (and even place the stent to fix it!). Searching for cancer cells?
A radiologist will help with that too.

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

### LAMP Stack
Many of our existing legacy applications are regular good 'ol LAMP stack
applications. The (L)inux (A)pache (M)ysql (P)HP stack is battle-tested for
sure. Most of the stuff we do is database-driven, and PHP and MySQL pair
together like a fine red wine and a ribeye steak.

Some of these applications are simple web dashboards written in PHP that
display relevant data from our MySQL database. For example, we've got one app
that allows staff to view statistics about our CT scanners and filter results.

Some of our these applications are "CRUD" apps that interact with our database.
CRUD stands for "Create, Replace, Update, and Delete." For example, physicians
earn merit and are paid based on different achievements and activities
throughout the year. We've developed a PHP application that allows the admin
staff to enter activities throughout the year. These are then added to a
database and ultimately a score is computed to help evaluate performance and
compensation.

We've got an application to request time and see availability on a particular
image scanner.

We've got a small application used for annual staff reviews.

These are just a few examples of our typical in-house PHP applications.

### Mobile Applications
Currently we only have one mobile application, but there are plans for more down
the line. It's an
[iOS app to calculate Gadolinum dosages](https://itunes.apple.com/us/app/gadcalc/id1051070769?mt=8).
It's written in Swift. It is used daily in the Hospital but we aren't currently
working on new features, only on maintenance. Porting the application to Android
is on our Summer road-map.

### Java and Groovy Grails
Finally, we've got a couple of legacy applications that are built in Java and
Apache's Groovy/Grails. At this point we have stopped all active development of
Java and Groovy/Grails applications outside of bug-fixes and regular
maintenance. The long-term plan is to port (update and re-write) these legacy
applications in our new unified tech-stack...**Ruby-on-Rails**.

## New applications

Ultimately, the nature of our department means we get a very wide range of
requests. Some 'application' requests are simple web-pages that have a dashboard
that displays data in some database. Other requests are more involved - like a
mobile app for calculating gadolinium dosages or an application that allows
Residents to compare their radiology reading room preliminary examinations to
an attending physician's final exam.

Going forward, the department has decided to simplify and unify our tech stack.
*Ruby-on-Rails* is our web framework of choice.

Why Ruby/Rails?
* Building new applications is wicked fast.
* It's suited to rapid agile development and other modern development practices.
* Code is highly readable, which is good when trying to hire and keep talented
development staff.
* Rails has a strong developer community.
* It's open source.

### (Philips)/AI Bridge Platform

[Analytical Informatics](https://www.analytical.info/developers/) (now owned by
Philips) provides a centralized platform for easily working with delicate
healthcare data. The [Bridge](https://developer-docs.analytical.info/) platform
is built on top of the Ruby-on-Rails framework (technically [jRuby](http://jruby.org/),
but let's not be pedantic).

By teaming up with the Philips/AI team, we can create applications that
interface with HL7 (Healthcare data standard) and DICOM (imaging standard) data
faster than ever.

### Wordpress

[Our website](https://radiology.wisc.edu) is a Wordpress website that follows
the conventions and uses the theming provided by the University of Wisconsin.
However it is developed and supported by our dev team. Most content updates are
done by the media/communication team, student employees, or specific
stakeholders.

## Infrastructure

Ahha! Now we get to the fun stuff. :smirk: My job as a dev/ops admin is to help
the other developers not worry about the infrastructure at all. I have to make
sure the application runs the same on our server(s) as it does on their local
development machine. 

### Servers

### Docker

### Database


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
