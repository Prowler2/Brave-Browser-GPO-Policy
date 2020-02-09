### Brave Browser GPO Policy Templates

I searched far and wide for GPO policy templates that would support managing Brave Browser in an Enterprise environment over the last few months with little success.

I did find a few github posts that revealed the location of single registry key tweaks that had to be manually applied, but often the location of those registry keys either followed the Chromium browser or Chrome browser standards and there was little consistency or automation options that could be leveraged in an enterprise.

One post in particular mentioned that since Brave Browser is based upon Chromium, that it would recognize and use the same registry policy keys. It was time to find out for myself.

In a lab environment I modified the original Google Chrome policy templates using an XML editor and successfully applied policy to Brave. Unfortunately you could only set one policy for all Chromium based browsers on a given system. There were also some specific registry keys (Disabling TOR) that only applied to Brave and had to be applied in a specific place. At best this was a fragmented and unrefined solution. 

As of release v1.3 (Feb 2020), Brave now has its own dedicated policy space in the registry separate from Chromium and Chrome.

On Windows, the location of Brave policy in the registry is:

 ###### Brave release 1.2 and older
`HKLM\SOFTWARE\Policies\Chromium`

###### Brave release 1.3 and newer
`HKLM\SOFTWARE\Policies\BraveSoftware\Brave`

I used the source Google Chrome Policy Templates v79.0.3945.130 and modified them to write to the Brave release 1.3 registry location instead. Additionally, I added some Brave specific policy for enabling/ disabling TOR that most enterprises would require to even consider deploying it.   
https://www.chromium.org/administrators/policy-templates

Details about each policy available in the Chrome source templates can be found at the link below
https://cloud.google.com/docs/chrome-enterprise/policies/

Modified Admin Policy Template added to the PolicyDefinitions directory on a windows machine. Policy namespace does not conflict with Chrome or other Chromium browsers.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveGPedit.PNG" alt="Brave GPO" />

Brave release 1.3 policy registry keys that were set by the modified admin template.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveRegistry.PNG" alt="Brave Registry" />

Brave policy page has detected and applied the policies.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BravePolicy.PNG" alt="Brave Policy" />

On the Brave Browser menu, TOR and In Private Browsing have been removed as set by policy. Note that Brave requires a restart of the browser for the TOR policy to take effect from my experience.   
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveMenu.PNG" alt="Brave Menu" />

On the Brave settings menu, notice that the ability to clear history is now managed.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveHistory.PNG" alt="Brave History" />

##### Warning!
**Please note I am not responsible for anything that may happen to your systems when using these templates! It is your responsibility to thoroughly test in an isolated environment before deploying them!**

Todo: 
1. Test and see which of the 300+ Chromium policies Brave still respects. This could take some time. 
2. Test the policy as applied to clients from a domain. 
3. ~~Make a GPO WMI filter to only apply policy if Brave is installed on the client machine.~~
4. Update Templates to the latest Chromium source version available. (v80.0.3987.87 as of 8 Feb 2020)
