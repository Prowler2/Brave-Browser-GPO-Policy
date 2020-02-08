### Brave Browser GPO Policy Templates

I searched far and wide for GPO policy templates that would support managing Brave Browser in an Enterprise environment over the last six months with little success.

There were a few github posts that would reveal the location of single registry keys for tweaks that had to be manually applied, but often the location of those registry keys either followed the Chromium browser or Chrome browser standards and there was little consistency or automation options that could be leveraged in an enterprise.

One post in particular mentioned that since Brave Browser is based upon Chromium, that it would recognize and use the same registry policy keys. 

In a lab environment I was able to modify the original Google Chrome policy templates and successfully make them work in this scenario. Unfortunately you could only set one policy for all Chromium browsers on a given system. There were also some specific registry keys (Disabling TOR) that only applied to Brave and had to be applied in a specific place. At best this was a fragmented and unrefined solution. 

As of release v1.3 (Feb 2020), Brave now has its own dedicated policy space in the registry separate from Chromium and Chrome.

On Windows, the location of Brave in the registry is:

 ###### Brave release 1.2 and older
`HKLM\SOFTWARE\Policies\Chromium`

###### Brave release 1.3 and newer
`HKLM\SOFTWARE\Policies\BraveSoftware\Brave`

I used the source Google Chrome Policy Templates and modified them to write to the Brave release 1.3 registry location instead. Additionally, I added some Brave specific policy for enabling/ disabling TOR that most enterprises would require to even consider deploying it. 
https://www.chromium.org/administrators/policy-templates

Details about each policy available in the Chrome source templates can be found at the link below
https://cloud.google.com/docs/chrome-enterprise/policies/

Manually added Brave registry keys for release 1.3 and newer
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/Brave%20Registry.PNG" alt="Brave Registry" />

Open the Brave Policy page. Brave has picked up and applied the three policies
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/Brave%20Policy.PNG" alt="Brave Policy" />

On the Brave Browser menu, TOR has been removed.

<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/Brave%20Menu.PNG" alt="Brave Menu" />

