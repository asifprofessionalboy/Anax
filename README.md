select ID,VendorCode,VendorName,PROC_MONTH,WorkOrderNo,WorkManCategory,Basic_DA_Wages,Department,
GrossWages,NoOfDaysWorked from App_PF_ESI_Details


select LocationCode  from App_Online_Wages_Details where VendorCode and PROC_MONTH=''

select Location from App_LocationMaster where LocationCode

select sex from App_EmployeeMaster where AadharCard 

