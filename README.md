# Intro

Description: This sheet generates random angles for the x and y axes to make vectors for a graph. The more iterations you tell it, the more detailed the graph becomes with the overall path depending on what happens on average. You can change what the min and max angle is generated for different types of graphs. I made this because I was learning vectors in AP physics and was having fun with it.

[Link to the sheet](https://docs.google.com/spreadsheets/d/1-E_FM7pGtT_SooirKjhYYa7__z5i6Tplh3cI4jLz5O0/edit?usp=sharing)

[How I made it](#how-i-made-it)

## Details
### Example 1
In the image are the main values you can change but you can change the actual formulas if you want.

![image](https://github.com/user-attachments/assets/b2458a5e-ddc6-4f83-95a1-c27cbdfda76d)

It generates these random vectors automatically when there is any change in the sheet.

![image](https://github.com/user-attachments/assets/d6d412aa-69fe-4ef0-af1e-dd7d73905b4e)

You can view the separate x and y positions and sometimes looks like a sort of crypto graph.

![image](https://github.com/user-attachments/assets/bc8a9e98-e271-4506-9da0-fc647be3ee23)

The result of x and y changing in this way creates this path starting from the origin:

![image](https://github.com/user-attachments/assets/e7732f5c-fcda-4b56-ae95-ef1014a17bbb)

### Example 2

Using a certain input and generating random examples gives me different types of graphs.

![image](https://github.com/user-attachments/assets/211091e8-9eef-4232-b0b4-5ac6abdf029a)
![image](https://github.com/user-attachments/assets/3cffcad8-fb8e-4401-bbb1-4e2011fbba67)
![image](https://github.com/user-attachments/assets/8e68d30e-7be4-42d2-8daf-a30e783deace)

### Example 3
Stocks are going crazy.

![image](https://github.com/user-attachments/assets/d8a63453-eb62-4840-9494-bfcf203b2450)
![image](https://github.com/user-attachments/assets/6235fe80-19b8-4956-af26-7a514562e3ed)

### Example 4
Only up to 45-degree angles are allowed.

![image](https://github.com/user-attachments/assets/8a5aa726-c1a3-46c0-be0e-f8638ef2eb53)
![image](https://github.com/user-attachments/assets/555fa0e1-865c-41ec-9f1d-89731fd3c230)

Apparently if you applied a force exactly like this, this is the direction it will end up.

![image](https://github.com/user-attachments/assets/f48b1ab9-8199-4130-9368-917c367a889f)

## How I made it

I generate random force and a random angle using this formula:

`=arrayformula(randarray(num)*(abs(minval)+abs(maxval))+minval)`

Then the x and y offsets are calculated by using this formula:

x `=arrayformula(if(isnumber(offset(force,0,0,num)),cos(offset(angle,0,0,num)*pi()/180)*offset(force,0,0,num),))`

y `=arrayformula(if(isnumber(offset(force,0,0,num)),sin(offset(angle,0,0,num)*pi()/180)*offset(force,0,0,num),))`

Then I use a running sum to get the real x and y positions

`=scan(0,offset(offset,0,0,num),lambda(a,b,a+b))`

After all this, the final graphs can be made.
