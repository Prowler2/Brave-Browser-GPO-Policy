### Brave Browser GPO Policy Templates

As of release v1.3 (Feb 2020), Brave now has its own dedicated policy space in the registry separate from Chromium and Google Chrome Browsers.

On Windows, the location of Brave policy in the registry for v1.3 and above is: `HKLM\SOFTWARE\Policies\BraveSoftware\Brave`

I used Google Chrome policy templates and modified them to use the Brave registry locations instead. Additionally, I added some Brave specific policies for TOR and IPFS that most enterprises would require to even consider deploying it. All current and future Brave specific policies will be located within the folder 'Brave Specific Policies'
https://www.chromium.org/administrators/policy-templates

Details about each policy available in the Chrome source templates can be found at the link below.
https://cloud.google.com/docs/chrome-enterprise/policies/

I created a Brave specific WMI filter for use with group policy. When this filter is attached to a GPO, it only applies the policy to clients where the WMI filter evaluates as true. (Clients where Brave Browser is installed). The filter and query were tuned and tested against client targets using the wmi filter validation tool here: 
http://sdmsoftware.com/gpoguy/free-tools/library/wmi-filter-validation-utility/

Modified source policy template added to the PolicyDefinitions directory on a Windows machine. Policy namespace does not conflict with Chrome or other Chromium browsers.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveGPedit.PNG" alt="Brave GPO" />

Brave policy registry keys that were set by the modified admin template.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveRegistry2.PNG" alt="Brave Registry" />

Brave policy page has detected and applied the policies.
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BravePolicy.PNG" alt="Brave Policy" />

On the Brave Browser menu, TOR and In Private Browsing have been removed as set by policy. Note that Brave requires a restart of the browser for the TOR policy to take effect from my experience.   
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveMenu.PNG" alt="Brave Menu" />

On the Brave settings menu, notice that the ability to clear history is now managed (greyed out).
<img src="https://github.com/Prowler2/Brave-Browser-GPO-Policy/blob/master/Images/BraveHistory.PNG" alt="Brave History" />

#### **Warning!**
**I am not responsible for anything that may happen to your systems when using these templates! It is your responsibility to thoroughly test in an isolated environment and understand what they do before deploying them!**
