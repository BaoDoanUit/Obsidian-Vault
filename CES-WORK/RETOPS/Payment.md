proc get list payment -- blu.usp_payment_select
```sql
-- step 1 
UnAllocatedAmount = UnAllocatedAmount = case when ba.clientIntID = 70 and isnull(p.acntID, 0) > 0 then 0 else  p.PaymentAmt - isnull(a.AllocatedAmount, 0) end

-- step 2
UnAllocatedAmount = p.UnAllocatedAmount - ISNULL(t.TransferAmount, 0),

-- table
blu.tbl_billing_account ba
blu.tbl_payment p
blu.tbl_payment_allocation a
```
![[Pasted image 20230413214843.png]]

proc get list payment -- blu.usp_payment_select
![[Pasted image 20230413215403.png]]
![[Pasted image 20230413215351.png]]