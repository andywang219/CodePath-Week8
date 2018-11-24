# CodePath-Week8
# Project 8 - Pentesting Live Targets

Time spent: **8** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Blue/SQLi.gif" alt = "sqli" />

Steps: 
First, go to the blue website. Second, go to the "Find a Salesperson" tab. Third, click on one of the salesperson. Last, at the end of the url, tack on ``` ' OR SLEEP(5)=0--' ```. After five seconds of waiting, the page will refresh and you will see a completely different salesperson.The other two websites will properly reroute you when attempting to do this.
<br/>

Vulnerability #2: Session Hijacking/Fixation
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Blue/SessionHijack.gif" alt = "hijack" />

Steps: 
First, open two separate browsers (eg Chrome and Firefox). On one of the browsers, go to the blue website and on the other the green website. Second, on the green website, log into your account. Third, in the green website, paste this: ``` /hacktools/change_session_id.php ``` at the end of the url. The url should then look like this: ``` https://35.184.88.145/green/public/hacktools/change_session_id.php ```. Fourth, do the same thing for the blue website except do not log in. The url should look like this ``` https://35.184.88.145/blue/public/hacktools/change_session_id.php ```. As you can see, the two session IDs are different. Now copy the session ID from the green website and paste it into the blue website (click "Change" afterwards). This allows you to bypass the login on the blue website.

## Green

Vulnerability #1: Username Enumeration
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Green/userEm.gif" alt = "user" />

Steps:
First, go to the green website and go to the login page. Second, try putting a random username and a random password. As you can see, the page throws an error. Now try logging in with pperson and a random password. The page throws an error again; however, this time its bolded. This tells you that the username exists. 


Vulnerability #2: Cross-Site Scripting (XSS)
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Green/xss.gif" alt = "xss" />

Steps:
First, go to the green website and go to the Contact tab. Second, fill out the information and for the Feedback section, input ``` <script>alert('Your Message');</script> ```. Third, log into your account and go to "Feedback". The moment you click on "Feedback", you'll see an alert with your message in it. The other two websites will display the message as text instead. 


## Red

Vulnerability #1: Cross-Site Request Forgery (CSRF)
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Red/forgery.gif" alt = "csrf" />

Steps:
First, log into your account on the Red website and go to the "Salesperson" tab. Second, download the testing.html file inside the Red folder. In the "Salesperson" tab, try to remember who's on there. Then open the html file that you've download. Upon opening the file, a new tab will open. Next, refresh the page and you should see that one of the name changed. 


Vulnerability #2: Insecure Direct Object Reference (IDOR)
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Red/IDOR.gif" alt = "idor" />

Steps:
First, log into your account on the Red website and go to the "Salesperson" tab. Find a person who's information cannot be viewed by the public yet and remember their ID. Second, log out of your account and go to "Find a Salesperson" tab. Here just click on a random person and in the url, change their ID to the one you just copied. After you hit enter, you can see that the link brings you to the page where the person's information should not be available is available. Now if you go back to "Find a Salesperson" and ctrl + F the person's name, you can see that they don't exist.

## Bonus Objective 2: Build on Objective #4 (Cross-Site Scripting)
<img src = "https://github.com/andywang219/CodePath-Week8/blob/master/Bonus/bonus.gif" alt = "xss2" />

Steps:
We follow the same steps as we did for Cross-Site Scripting (XSS). However, this time in the "Feedback" section, you put ``` <script>document.location="https://www.google.com/"</script> ``` rather than a message. This will redirect the person to the link you inputed when they open the feedback.

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Andy Wang]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
