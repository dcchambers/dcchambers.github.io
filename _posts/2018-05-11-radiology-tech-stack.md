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
CRUD stands for "Create, Read, Update, and Delete." For example, physicians
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
**Ruby-on-Rails** is our web framework of choice.

![](/assets/images/ruby-rails.png)

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

![](/assets/images/analytical-info.png) ![](/assets/images/philips.png)

Why is working on the Philips/AI Bridge platform so great? Here's a couple
reasons.
* **Real-Time Normalized Database.** We work with a lot of data from a lot of
different sources. They aggregate that data, validate it, and let us access it
with stupid simple queries.
* **HIPAA Audit Logging.** HIPAA isn't anything to mess with. A single failure can
cost your company/hospital/university millions. Writing code to log everything
for future potential audits isn't so fun either.
* **Authentication.** They tap into our Active Directory for Single Sign On and
also allow integration with PACS and other clinical applications.
* **Share with others.** We can tap into applications that other groups have
built on the Bridge platform and use/extend them as we need. We can also share
what we have done with others! Sharing is caring! :wave:

*TL;DR - they take care of the boring stuff and let us ship apps in record time!*

Ruby on Rails! *In 2018?!* Of course :wink: I'm sure I'll write more on this later.


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

The infrastructure team at UW Health provides IaaS (Infrastructure as a Service)
to various teams within UW Health and the UW School of Medicine. They host all
of our VMs in highly reliable, distributed data-centers that are designed for
maximum uptime.

### Servers

All of our servers run some flavor of Linux. Most of what we've got deployed
right now is RHEL7/CentOS7, with some CentOS6 and Ubuntu 16.04 Server boxes in
the mix.

### Docker

![](/assets/images/docker.jpg)

Containerize all the things! If you don't know what
[Docker](https://www.docker.com/) or
[containers](https://www.redhat.com/en/topics/containers) are - you're really
missing out. We have all of our applications "dockerized." In practice, this
means we use docker-compose to build and run the application environment.

Perhaps the best advantage to working in a Docker
environment is that everything is highly portable. If it runs docker, it should
be able to run your application without issue - no matter what kind of
dependency hell you've created or what strange version of Ruby or MySQL you
need to get your application working.

### Deployment

![](/assets/images/jenkins.png)

We use [Jenkins](https://jenkins.io/) to manage our application building and to
automate deployment to development, testing, and production environments. I get
to spend a good chunk of my time working with Docker and Jenkins!

### Database

Our primary database is MySQL, which works great with the web-focused
tools and applications we create.

The Philips/AI database is PostgreSQL.

### Everything Else
#### Nginx
We use Nginx as a [reverse proxy](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/).
#### Apache
Many of our legacy applications use the Apache web server.
#### LDAP
We support a number of login methods, including non-domain accounts and
integration with UW Health's Active Directory domain using LDAP.
#### Version Control
Our legacy applications are set up in Mercurial Repos using
[Kiln](http://help.fogcreek.com/kiln).

We use Git for current and future applications, and have a self-hosted
[Github Enterprise](https://enterprise.github.com/home) account. We also keep
all of our docker/container configuration in Git. Not using Git?
[You should be.](http://chambers.io/2018/04/09/git-101.html)

---

And that's just about everything. As you can see, we use a ton of different
technologies and get to work on a wide range of applications. It can get a
little crazy at times, but it's awesome that we get to learn so many cool
tools/technologies and see many projects through from start-to-finish. There
aren't many jobs where you get to meet with primary stakeholders and go through
the entire development process from start to finish. It's also nice knowing that
the stuff we work on is being used to directly improve both patient healthcare
and medical research.
