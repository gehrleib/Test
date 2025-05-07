Hey Matt,

Just wanted to flag an issue we've been seeing in Production where all our regroups are being archived. After digging into it, I've pinpointed two recurring problems:

We're hitting "Request Failed" errors with an HTTP 520 status code.
The API call is successful, but it's returning empty responses.
That second issue is particularly tricky. When we get nothing back, our current process interprets it as the RegGroup being unavailable (like it was deleted), and we automatically archive it. This has a knock-on effect: any assessable units linked to those RegGroups get automatically delinked.

To address the empty response issue, we need to make a change to our script before we onboard more users. The plan is to treat an empty response as an error and stop the script.

In the meantime, I'm hoping you can get the CUBE team involved to investigate the root cause of both the HTTP 520 errors and the empty responses. Unless something has changed on their end that we weren't made aware of, our script is configured with the following details:

&lt;insert endpoints and username>

Could you please let me know if this is something CUBE can look into? 
