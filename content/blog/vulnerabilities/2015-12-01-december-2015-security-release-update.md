---
title: December Security Release Schedule Update
blogAuthors: ['rvagg']
category: 'vulnerabilities'
---

The OpenSSL project [announced](https://mta.openssl.org/pipermail/openssl-announce/2015-November/000045.html) today that they will be releasing security updates for versions 1.0.2, 1.0.1, 1.0.0 and 0.9.8 on the 3rd of December UTC. The updates will fix a number of security defects, the highest of which is classified as "moderate" severity according to their [severity scale](https://www.openssl.org/policies/secpolicy.html):

> MODERATE Severity. This includes issues like crashes in client applications, flaws in protocols that are less commonly used (such as DTLS), and local flaws. These will in general be kept private until the next release, and that release will be scheduled so that it can roll up several such flaws at one time.

Node.js versions v0.10.x and v0.12.x depend on OpenSSL v1.0.1 and versions v4.x (LTS Argon) and v5.x depend on OpenSSL v1.0.2. As the Node.js build process statically links OpenSSL into binaries, we will be required to release patch-level updates to all of our actively supported versions to include the upstream fixes. While we are unaware of the exact nature of the OpenSSL vulnerabilities being fixed, we must consider it likely that Node.js releases will be required in order to protect users.

Since the OpenSSL release schedule is two days after our [announced updates](https://groups.google.com/forum/#!topic/nodejs-sec/Zf7Nxtg230E) for v0.12.x, v4.x and v5.x, we have decided to **postpone our security releases to coincide with OpenSSL release availability**. We will also be **including v0.10 in our set of releases**.

Therefore, we are moving our planned security releases for Node.js from Wednesday the 2nd of December 2015, UTC to the **Friday, the 4th of December 2015, UTC** _(Thursday the 3rd of December US time)_. We understand that the timing of this during the work-week is unfortunate but we must take into account the possibility of introducing a vulnerability gap between disclosure of OpenSSL vulnerabilities and patched releases by Node.js and therefore must respond as quickly as practical. Please be aware that patching and testing of OpenSSL updates is a non-trivial exercise and there will be significant delay after the OpenSSL releases before we can be confident that Node.js builds are stable and suitable for release.

An updated summary of the release inclusions is available below:

***

## CVE-2015-8027 Denial of Service Vulnerability

A bug exists in Node.js, all versions of v0.12.x through to v5.x inclusive, whereby an external attacker can cause a denial of service. The severity of this issue is high and users of the affected versions should plan to upgrade when a fix is made available.

* Versions 0.10.x of Node.js are _**not affected**_.
* Versions 0.12.x of Node.js are _**vulnerable**_.
* Versions 4.x, including LTS Argon, of Node.js are _**vulnerable**_.
* Versions 5.x of Node.js are _**vulnerable**_.

## CVE-2015-6764 V8 Out-of-bounds Access Vulnerability

An additional bug exists in Node.js, all versions of v4.x and v5.x, whereby an attacker may be able to trigger an out-of-bounds access and/or denial of service if user-supplied JavaScript can be executed by an application. The severity of this issue is considered medium for Node.js users, but only under circumstances where an attacker may cause user-supplied JavaScript to be executed within a Node.js application. Fixes will be shipped for the v4.x and v5.x release lines along with fixes for CVE-2015-8027.

* Versions 0.10.x of Node.js are _**not affected**_.
* Versions 0.12.x of Node.js are _**not affected**_.
* Versions 4.x, including LTS Argon, of Node.js are _**vulnerable**_.
* Versions 5.x of Node.js are _**vulnerable**_.

## OpenSSL Moderate Severity Update

The OpenSSL project has [announced](https://mta.openssl.org/pipermail/openssl-announce/2015-November/000045.html) a set of releases which contain fixes for multiple vulnerabilities, the highest severity being labelled "moderate". Consult the [OpenSSL security policy](https://www.openssl.org/policies/secpolicy.html) for details on this definition. New releases of all actively maintained Node.js release lines are required in order to protect users against potential vulnerabilities in their applications. We do not have details on the nature of any of the included vulnerabilities or their fixes, users should plan for upgrades as soon as practical.

* Versions 0.10.x of Node.js _**may be vulnerable**_.
* Versions 0.12.x of Node.js _**may be vulnerable**_.
* Versions 4.x, including LTS Argon, of Node.js _**may be vulnerable**_.
* Versions 5.x of Node.js _**may be vulnerable**_.