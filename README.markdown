SPMon: Service Provider Monitoring
==================================

What is it?
-----------

SPMon is a collection of simple scripts that are meant to be plugged
in various monitoring systems to query service provides for some data.

For example, if you use an Internet service provider, pay for it and
want to collect account balance stats on regular basis, you'd most
likely want to query programmatically from your monitoring system (for
example, once per day) to check that your account balance approaches
critical level that would mean termination of services and thus
trouble.

Unfortunately, most service providers don't provide APIs to get
interesting data from them - so we're most usually end up emulating a
web browser that opens a log in page, enters credentials in some form,
submits that form, clicks a few buttons around and then comes up with
the data we want.

What can be monitored?
----------------------

* Internet service providers
* Web hosting service providers
* Domain registrars
* Cell phone providers
* VOIP providers
* E-commerce payment systems
* Banking accounts
* ... etc

If provider uses pre-paid scheme, then SPMon scripts would usually
return account balance (which usually decreases with time, as more and
more services are rendered). If provider uses subscription services
with per-period fee, then SPMon scripts would usually reports paid
time left in currently paid period.

How to use it?
--------------

* Choose a directory in `services/` directory by your service
provider's hostname.
* Check README file in that directory or just script's sources for a
list of parameters required for a given script.
* Pass required parameters (usually scripts require credentials to log
in to service providers) as environment variables, i.e.:

    LOGIN=some-login PASSWORD=s0m3-p4ssw0rd ./monitor

* If everything's okay, script would output result at stdout.
