<h1 align="center">
  <br>
  <a href=""><img src="/img/logo.png" alt="" width="300px;" height="100px"></a>
  <br>
  <img src="https://img.shields.io/badge/PRs-welcome-blue">
  <img src="https://img.shields.io/github/last-commit/kh4sh3i/Grafana-CVE"> 
  <img src="https://img.shields.io/github/commit-activity/m/kh4sh3i/Grafana-CVE">
  <a href="https://twitter.com/intent/follow?screen_name=kh4sh3i_"><img src="https://img.shields.io/twitter/follow/kh4sh3i_?style=flat&logo=twitter"></a>
  <a href="https://github.com/kh4sh3i"><img src="https://img.shields.io/github/stars/kh4sh3i?style=flat&logo=github"></a>
</h1>

# Grafana-CVE
a Curated list of Grafana Security Vulnerabilities, CVE & exploit


## What Is Grafana? 
Grafana is a multi-platform open source analytics and interactive visualization web application. It provides charts, graphs, and alerts for the web when connected to supported data sources


## CVE-2020-11110
Grafana through 6.7.1 allows stored XSS due to insufficient input protection in the originalUrl field, which allows an attacker to inject JavaScript code that will be executed after clicking on Open Original Dashboard after visiting the snapshot.

```url
https://target/api/snapshots
```


## CVE-2021-43798
 Grafana versions 8.0.0-beta1 through 8.3.0 (except for patched versions) iss vulnerable to directory traversal, allowing access to local files. The vulnerable URL path is: `<grafana_host_url>/public/plugins//`, where is the plugin ID for any installed plugin.

 ```url
https://target/public/plugins/alertlist/../../../../../../../../../../../../../../../../../../../etc/passwd
 ```


## CVE-2021-41174
 In affected versions if an attacker is able to convince a victim to visit a URL referencing a vulnerable page, arbitrary JavaScript content may be executed within the context of the victim's browser. The user visiting the malicious link must be unauthenticated and the link must be for a page that contains the login button in the menu bar. The url has to be crafted to exploit AngularJS rendering and contain the interpolation binding for AngularJS expressions. AngularJS uses double curly braces for interpolation binding: {{ }} ex: {{constructor.constructor(‘alert(1)’)()}}. When the user follows the link and the page renders, the login button will contain the original link with a query parameter to force a redirect to the login page. The URL is not validated and the AngularJS rendering engine will execute the JavaScript expression contained in the URL. 

 ```url
 https://target/dashboard/snapshot/%7B%7Bconstructor.constructor(%27alert(document.domain)%27)()%7D%7D?orgId=1
 ```


 ## CVE-2021-39226
In affected versions unauthenticated and authenticated users are able to view the snapshot with the lowest database key by accessing the literal paths: /dashboard/snapshot/:key, or /api/snapshots/:key. If the snapshot "public_mode" configuration setting is set to true (vs default of false), unauthenticated users are able to delete the snapshot with the lowest database key by accessing the literal path: /api/snapshots-delete/:deleteKey. Regardless of the snapshot "public_mode" setting, authenticated users are able to delete the snapshot with the lowest database key by accessing the literal paths: /api/snapshots/:key, or /api/snapshots-delete/:deleteKey. 

```url
https://target/api/snapshots/:key
```


## CVE-2021-27358
The snapshot feature in Grafana 6.7.3 through 7.4.1 can allow an unauthenticated remote attackers to trigger a Denial of Service via a remote API call if a commonly used configuration is set.

```url
https://target/api/snapshots
```


## CVE-2022-32275
Grafana 8.4.3 allows reading files via (for example) a /dashboard/snapshot/%7B%7Bconstructor.constructor'/.. /.. /.. /.. /.. /.. /.. /.. /etc/passwd URI.

```url
 https://target/dashboard/snapshot/%7B%7Bconstructor.constructor'/.. /.. /.. /.. /.. /.. /.. /.. /etc/passwd
```


## CVE-2022-32276
** DISPUTED ** Grafana 8.4.3 allows unauthenticated access via (for example) a /dashboard/snapshot/*?orgId=0 URI. NOTE: the vendor considers this a UI bug, not a vulnerability.

```url
https://target/dashboard/snapshot/*?orgId=0
```


## Grafana Enterprise Metrics
Metrics tell you how much of something exists, such as how much memory a computer system has available or how many centimeters long a desktop is. In the case of Grafana, metrics are most useful when they are recorded repeatedly over time.

```url
https://target/metrics
```


## referencess
* [Grafana : Security Vulnerabilities](https://www.cvedetails.com/cve/CVE-2022-32276/)