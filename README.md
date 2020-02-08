### Brave Browser GPO Policy Templates

I searched far and wide for GPO policy files to support managing Brave Browser in an Enterprise environment over the last six months with little success.

There were a few github posts that would reveal the location of single registry keys for tweaks that had to be manually applied, but often the location of those registry keys either followed the Chromium browser or Chrome browser standards and there was little consistency or automation options.

One post in particular mentioned that since Brave Browser is based upon Chromium, that it would recognize and use the same registry policy keys.  In a lab environment I was able to modify the Google Chrome policy templates and successfully make them work in this scenario. Unfortunately you could only set one policy for all Chromium browsers on a given system. There were also some specific registry keys (Disabling TOR) that only applied to Brave and had to be applied in a specific place. At best this was a fragmented and unrefined solution. 

As of release v1.3, Brave now has its own dedicated policy space in the registry separate from Chromium and Chrome.

On Windows, the location of Brave registry policy is:

 ###### Brave release 1.2 and older
`HKLM\SOFTWARE\Policies\Chromium`

###### Brave release 1.3 and newer
`HKLM\SOFTWARE\Policies\BraveSoftware\Brave`

I used the source Google Chrome Policy Templates and modified them to write to the Brave 1.3 registry area instead. Additionally, I added some Brave specific policy for enabling/ disabling TOR that most enterprises would require to even consider deploying it. 
https://www.chromium.org/administrators/policy-templates
