 Add code to the <Bill Consumer Name>to include logic for <Provide description of new functionality being requested>.

For example, a new charge or calculation needs to be added.

Additional information related to invoicing needs to be stored.

Create new tables, fields or flags to indicate whether new functionality applies.

This should include all the following processes which calculate invoices to ensure that there is only one code base to maintain.

Dual-Billing

Resettlement

Bill-Ready

All logic related to invoice generation should remain the same.  All other logic should remain the same and impacted tables should still populate according to existing code.

There should be no significant negative impact on performance.

All other downstream processes should be complete successfully.