Script I use to manage my CyberPower UPS. The goal of the script is to handle overload events, which cannot be automatically handled by pwrstat. 


At first, I tried to solve this with claude. Here is a link to the chat: https://claude.ai/share/18a718dc-b5b1-4b16-8298-c8edf54e6e18

Honestly, I'm pretty disappointed with Claude. I was pretty explicit with my requirements, but it kept making pretty bad mistakes. The small time accumulation mistake during intitial overload is excusable since it probably wouldn't have any effect, but failing to account for the case where the power goes above the HIGH_BAND and then hovers between the LOW_BAND and HIGH_BAND is a pretty big mistake, especially since not checking for this condition kind of defeats the purpose of having a separate LOW_BAND. Requirements 2 and 3 also explicitely explain this behavior. Then, when fixing this, it failed to account for another small time accumulation error that led to overestimated cumulative overload times. Then, when I pointed it out and it tried to fix the issue, it terribly broke continuous overload protection by resetting continuous_overload_start every single time the power flucuates around HIGH_BAND, even when it doesnt fall below LOW_BAND. I'm scared its going to break even more stuff if I ask it to fix this, and the whole point of using AI was to get this done quicker, so I am giving up on Claude for now. 


Next, I plan to try Codex using a prompt setup I used with Claude. Once I get the whole subscription stuff figured out, I will give it a try.