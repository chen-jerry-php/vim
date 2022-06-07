#### Vulnerability title: <br>
Bypassing the xss defense by uploading files at the user-added place causes the storage of xss

#### Affected versions:<br>
Premium v4.0.1.1477

### Discovery time: <br>
2022/06/07

### Found by:<br>
jerryflag

### analysis report: <br>
0x01:<br>
First, I found that this program is vulnerable to stored xss attacks. When I communicated with the program provider, I was told that the program has xss protection, so I bypassed the xss protection through further attempts and made my xss attack effective
![image](https://user-images.githubusercontent.com/52393447/172317236-3050a9d3-93a0-40f6-abb7-a5a16a3b05eb.png) <br>
0x02:<br>
It was observed that the program has a batch add function, so add the payload to the excel file, simulate the batch add user function, bypass the xss protection, and make the xss attack take effect.
![image](https://user-images.githubusercontent.com/52393447/172321335-34ea1a53-b12b-476a-a26c-4d45bed55742.png)
poc: <br>
`<img src=1 onerror=alert(1)>`<br>
`<img src=1 onerror=alert(2)>`
![image](https://user-images.githubusercontent.com/52393447/172321762-8db7ea76-1567-4ea9-8183-19d3f2d8d2f9.png)
0x03:<br>
The page automatically loads and triggers XSS<br>
The final xss effective result<br>
![image](https://user-images.githubusercontent.com/52393447/172324760-d9215fc4-1272-49b5-ac7a-aa879b3fe99d.png)
![image](https://user-images.githubusercontent.com/52393447/172325449-6e6bb6d7-bc51-4d92-9f41-e3bd7794ec77.png)
![image](https://user-images.githubusercontent.com/52393447/172324841-6c33bac7-e484-4830-bd18-2ad1c33edd9d.png)
![image](https://user-images.githubusercontent.com/52393447/172325355-4da0602a-134d-46e7-a91e-798d3f528439.png)

### Fixes: <br>
Make xss protection fully effective

### illustrate
(1) http://www.urtracker.cn/ , 
#### Introduction to URTracker
"URTracker transaction tracking tracking system" is a general problem (Issue Tracking) software for these problems. It is used to help businesses and teams create various types of processes, manage all of them and keep track of recorded processes, and has a built-in workbench for sharing issues.<br>
(2) Reproduce the demo
url：http://www.1.urtracker.cn/Accounts/login.aspx?ReturnUrl=%2fdefault.aspx
account/passwprd：admin/123456
