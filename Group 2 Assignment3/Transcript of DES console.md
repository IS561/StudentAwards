### Step1: consult the console
Warning: Y>=50 may raise a computing exception if non-ground at run-time.  
Warning: Next rule is unsafe because of variable: [Y]  
gt50(Y) :-  
Y>=50.  
Warning: Y<500 may raise a computing exception if non-ground at run-time.  
Warning: Next rule is unsafe because of variable: [Y]  
st500(Y) :-  
Y<500.  
Warning: Y<50 may raise a computing exception if non-ground at run-time.  
Warning: Next rule is unsafe because of variable: [Y]  
st50(Y) :-  
Y<50.  
  
**Screenshot**  
<img src="https://user-images.githubusercontent.com/46877258/55187739-cb8ce280-5167-11e9-8124-61be90b22bc8.png" width="400" height="210">
***
### Step2: check provostApprove, deanApprove and isSelfSupporting
DES> provostApprove(kbea)  
{  
  provostApprove(kbea)  
}  
Info: 1 tuple computed.  
  
DES> deanApprove(kbea)  
{  
  deanApprove(kbea)  
}  
Info: 1 tuple computed.  
  
DES> isSelfSupporting(kbea)  
{  
  isSelfSupporting(kbea)  
}  
Info: 1 tuple computed.  
  
**Screenshot**  
<img src="https://user-images.githubusercontent.com/46877258/55187981-40f8b300-5168-11e9-8904-be35cafe64e1.png" width="150" height="300">
***
### Step 3: check whether KBEA is a category 2 award (computing 1 tuple means KBEA is category 2)
DES> is_category2_gt50(kbea,100)  
{  
  is_category2_gt50(kbea,100)  
}  
Info: 1 tuple computed.  
  
**Screenshot**  
<img src="https://user-images.githubusercontent.com/46877258/55188973-ac438480-516a-11e9-80da-49c3a3a9e9e2.png" width="190" height="100">
***
### Step 4: check whether small prize is a category 2 award (computing 1 tuple means small prize is category 2)
#### We created an award named "small prize". It is $10, self supporting and approved by on the dean.
DES> is_category2_st50(small_prize,10)  
{  
  is_category2_st50(small_prize,10)  
}  
Info: 1 tuple computed.      
  
**Screenshot**  
<img src="https://user-images.githubusercontent.com/46877258/55189245-620ed300-516b-11e9-90d4-89b47a45b0b8.png" width="220" height="100">

Referred source: https://ardalis.com/add-images-easily-to-github (how to add images to GitHub)
