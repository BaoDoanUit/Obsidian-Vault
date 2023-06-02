
### Proc [dbo].[usp_Process_814_Add_Trans]

- Data from Table tbl_ESG_EDI_Transaction & tbl_ESG_EDI_GAA_Account with Processed <> 1
    - ESP Account Number	LDC Account Number
    - 42620156220216	08040529380000567720
    - NULL	0550090066977000585691
- Data from Table tbl_ESG_EDI_Transaction & tbl_ESG_EDI_GAA_Account with Processed = 1
     - ESP Account Number	LDC Account Number
     - 00224829	0550056658437001626574
     - NULL	PE000008769063244166

### PROCEDURE [blu].[usp_enroll_request_merge]
![[UdcAcntNumb.png]]

### PROC [blu].[usp_enroll_request_batch_process_bulk]
table : fil.tbl_enroll_request_batch_staging_bulk





