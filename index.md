---
title: Welcome to Stitch Documentation
layout: page-no-edit
toc: false
permalink: index.html
summary: "Guides and resources for setting up and managing your Stitch data pipeline."
---
{% include misc/data-files.html %}

<p class="intro">{{ site.description }} Not using Stitch yet? Start your <a href="https://www.stitchdata.com/signup/">free trial.</a></p> 
<hr />

<h2>Getting Started</h2>
<ul class="columns more">
	<li><a href="{{ link.getting-started | prepend: site.baseurl }}">Getting Started Guide</a></li>
	<li><a href="{{ link.destinations.main | prepend: site.baseurl }}">Destinations</a></li>
	<li><a href="{{ link.integrations.main | prepend: site.baseurl }}">Integrations</a></li>
	<li><a href="{{ link.account.team-members | prepend: site.baseurl }}">Adding/Removing Team Members</a></li>
	<li><a href="{{ link.billing.billing-guide | prepend: site.baseurl }}">Understanding Your Usage & Billing</a></li>
	<li><a href="{{ link.account.security-faq | prepend: site.baseurl }}">Security</a></li>
	<li><a href="{{ site.baseurl }}/tag_getting_started">More</a></li>
</ul>
<hr />

<h2>Replicating Data</h2>
<ul class="columns more">
	<li><a href="{{ link.replication.overview | prepend: site.baseurl }}">Stitch's Replication Process</a></li>
	<li><a href="{{ link.replication.rep-methods | prepend: site.baseurl }}">Replication Methods</a></li>
	<li><a href="{{ link.replication.rep-keys | prepend: site.baseurl }}">Replication Keys</a></li>
	<li><a href="{{ link.replication.rep-frequency | prepend: site.baseurl }}">Replication Frequency</a></li>
	<li><a href="{{ link.destinations.storage.stitch-schema | prepend: site.baseurl }}">Integration Schemas</a></li>
	<li><a href="{{ link.replication.main | prepend: site.baseurl }}">More</a></li>
</ul>
<hr />

<h2>Troubleshooting</h2>
<ul class="columns more">
	<li><a href="{{ link.troubleshooting.dw-connection-errors | prepend: site.baseurl }}">Destination Connection Issues</a></li>
	<li><a href="{{ link.troubleshooting.db-connection-errors | prepend: site.baseurl }}">Database Connection Issues</a></li>
	<li><a href="{{ link.troubleshooting.saas-connection-errors | prepend: site.baseurl }}">SaaS Integration Connection Issues</a></li>
	<li><a href="{{ link.troubleshooting.discrepancy-guide | prepend: site.baseurl }}">Data Discrepancy Guide</a></li>
	<li><a href="{{ link.troubleshooting.errors | prepend: site.baseurl }}">Error Notifications</a></li>
	<li><a href="{{ link.troubleshooting.billing-issues | prepend: site.baseurl }}">Billing Issues</a></li>
	<li><a href="{{ link.troubleshooting.main | prepend: site.baseurl }}">More</a></li>
</ul>
<hr />

<h2>Resources</h2>
<ul class="columns">
	<li><a href="{{ site.resources }}">Stitch Resources</a></li>
	<li><a href="{{ site.status }}">Stitch Status</a></li>
	<li><a href="{{ site.changelog }}">Changelog</a></li>
	<li><a href="{{ site.blog }}">Blog</a></li>
</ul>
