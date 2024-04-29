#### Table
retail_billing.bil.tbl_resettlement_data_check
retail_billing.bil.tbl_resettle_calc
retail.blu.tbl_invoice_adjustments
retail_billing.bil.tbl_invoice_detail
retail_billing.bil.tbl_invoice

#### Stored Procedure
retail_billing.bil.usp_resettlement_data_check_insert 
- insert new records where InvoiceIDApplied select invoiceid from bil.tbl_invoice (nolock) where (stmtid = @StmtID or invoiceid =@InvoiceID) and invoice_status_id<>3
retail_billing.bil.usp_billing_VoidInvoice

retail_billing.bil.usp_statement_combination
- 