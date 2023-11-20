https://ces-ltd.atlassian.net/browse/RETINV-1602

Query
select * from [ETHDB01.CES-LTD.COM].[BlueEthical_Prd].[dbo].tbl_invoice_outbound b
where DataRefID in (15773986,
15774003,15774035,15774036,15774053,
15774069,15774070,15774137,15774167)

select * from retail.blu.tbl_invoice_out
where InvoiceOutID in (15773986,
15774003,15774035,15774036,15774053,
15774069,15774070,15774137,15774167)

select * from retail_amazon_ethical.[dbo].[tbl_data_extract] 
where Name = 'Ethical Invoice Outbound - Prod'