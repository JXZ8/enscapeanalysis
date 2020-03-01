# EnCrack 
## Enscape vulnerability analysis (simplified version)
The following steps reveal the potential vulnerabilities  that Enscape may have

### Start IDA
First, start IDA and load Enscape.Common.dll.
![1.png](/pics/1.png)

### Trying To Get License Status Code
1.ALT+T -> search key string "expired"
![2.png](/pics/2.png)
2.Results
![3.png](/pics/3.png)
3.Click the second or third one
![4.png](/pics/4.png)
4.Now, all license status codes are shown.

### Using CE To Access Memory
1.First, let's start Enscape trial, and search "1" (license status code).  
![6.png](/pics/6.png)  
2.Make trial expired, search "2".  
![7.png](/pics/7.png)  
3.Repeating step 1 and 2, and we can get the address where license status stored.  
![8.png](/pics/8.png)  
4.Click "Find out what writes to this address".  
![9.png](/pics/9.png)  
5.Now we make the status code change again, and then we can get the assembly code that changes the status code.   
![10.png](/pics/10.png)  
![11.png](/pics/11.png)  
![12.png](/pics/12.png)  
6.Because the assembly code is generated dynamically, so we need the signature code. The signature code is "C7 46 68 \[STATUS CODE]". (Actually the signature is 0x74,0x10, 0xC7, 0x46, 0x68, 01/02,00,00).  
7.Now if we change the signature code to C7 46 68 00, we can fully activate Enscape(Or we can use hooking technique).  
![21.png](/pics/21.png)  
![20.png](/pics/20.png)  

