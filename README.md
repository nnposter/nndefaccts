# NNDefaccts

## TL;DR
[NNdefaccts](https://github.com/nnposter/nndefaccts/) is nnposter's alternate fingerprint dataset for Nmap script http-default-accounts.

## Overview
One of [Nmap](https://nmap.org/) scripts, [http-default-accounts](https://nmap.org/nsedoc/scripts/http-default-accounts.html), can be used to test a web target for presence of default credentials specific to various platforms, applications, and management interfaces. The script relies on a fingerprint dataset for correctly identifying the target and performing a login sequence.

Nmap comes with its own default fingerprint dataset; there is no inherent necessity to seek an alternative, such as this one. The key difference is that the NNdefaccts dataset is much larger so many more target types can be tested. Note though that this dataset is not provided, licensed, supported or endorsed by the Nmap project.

To various degrees, checking for default credentials is possible with other well-recognized tools besides Nmap: Metasploit, OpenVAS, Nessus, Qualys, Nexpose, Acunetix, and similar. Based on our evaluation, Nmap with the NNdefaccts dataset is one of the best with respect to web interfaces. Compared to some, it is an order of magnitude difference.

## Installation, Usage
For simple one-off use, just copy file `http-default-accounts-fingerprints-nndefaccts.lua` to your home directory and, instead of running:
```
nmap --script http-default-accounts -p 80 192.168.1.1
```
add `--script-args http-default-accounts.fingerprintfile=...` to the command line:
```
nmap --script http-default-accounts --script-args http-default-accounts.fingerprintfile=~/http-default-accounts-fingerprints-nndefaccts.lua -p 80 192.168.1.1
```
For more permanent use, you might consider replacing the default fingerprint dataset with this one. The default dataset is typically installed as `/usr/share/nmap/nselib/data/http-default-accounts-fingerprints.lua` (on Linux).

## Support
For help with running script http-default-accounts or Nmap in general, see https://nmap.org/.

For issues specific to NNdefaccts, see below.

## Contributing
Contributions are appreciated but please review the rest of the section first.

### Bug Reports
Identifying and reporting issues in the dataset is highly valuable. If you believe that you have found a defect, please make sure that you are using the latest version of the dataset and review currently open issues on GitHub to verify that the defect has not been already submitted. If not, create a new issue and be as specific as possible to help with reproducing the problem.

In many cases it is necessary to capture and inspect relevant HTTP traffic in detail. Please use [ZAP](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project), [Fiddler](https://www.telerik.com/download/fiddler) or [Burp](https://portswigger.net/burp) to capture the traffic and send the resulting session/project file to nndefaccts /at/ shared-files.de, referencing the issue. (Do not upload the file to GitHub because of its potentially sensitive content.)

### Code Contributions
Patches for fixing defects are welcome. Please note that by submitting any code related to the dataset to the NNdefaccts repository or passing it onto nnposter by other means you are assumed to have granted nnposter unlimited, irrevocable, perpetual non-exclusive license to the code, including reuse, modification, and relicensing.

### Fingerprint Contributions
All fingerprints included in the dataset are developed and quality-tested against real targets. As a result, it is not currently possible to contribute new fingerprints directly, as a code. If your particular target is not covered by the dataset but you have access to a target instance and able to log in with its default credentials then you can instead contribute by submitting an HTTP session file, capturing the login.

Please send a Fiddler, Burp, or ZAP session file to nndefaccts /at/ shared-files.de, prepared as follows:
1. Close any browser tabs with the target loaded.
1. Clear your browser cache, cookies, and local storage.
1. Visit the target top/home page, navigate to the login page, and log in with the correct default username but obviously wrong password, such as "wrongpassword".
1. Repeat the first three steps but log in with the correct username and password.
1. Name the file vendor-product-version, such as Apache-Tomcat-8.0.saz.
1. Send it to the above-mentioned e-mail.

## Author, License
NNdefaccts is Copyright (c) 2012-2018 by nnposter (nnposter /at/ users.sourceforge.net, https://github.com/nnposter), a party separate from Fyodor, Nmap Project, and Insecure.Com, LLC.

NNdefaccts is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

For details see the full license at [COPYING](https://github.com/nnposter/nndefaccts/blob/master/COPYING).
