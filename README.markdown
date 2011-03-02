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
* If you want to install a given script somewhere permanently, note
that all scripts require "_spmon_lib" file with common functions and
initializations. You have 2 options:
  * Either copy required script (`services/xxx/monitor`) and common
  functions file (`services/_spmon_lib`) in the same directory,
  * Or put common functions file somewhere in PATH
  (i.e. `/usr/local/bin`, `/usr/bin`, etc) where it can be found.

Philosophy
----------

SPMon scripts are designed to be:

* Simple - most scripts consist of 5-6 lines of code and thus should
be easy to understand, support and maintain.
* Minimalistic - most scripts "emulate" browser behavior when logging
in to the provider's site and checking the requested data, but this
emulation shouldn't be considered full and accurate. Throughout
emulation of real human behavior is a fairly complex task and
generally contradicts other goals of SPMon project.
* Portable - SPMon's scripts require only basic UNIX shell and some
application (currently wget). It should be easy to run SPMon scripts
in Linux, BSD and Windows systems.
* Work out of box (with no or minimal configuration).
* Easy to embed in most monitoring systems - most systems allow
running external scripts that report values using stdout.
* Easy to reuse - several lines of code in every script clearly
designate HTTP requests that are required to perform a task and thus
these requests could be easily implemented in all possible languages.

License
-------

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or (at
your option) any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.org/licenses/>.
