SELECT Top 100
CONCAT(WG.YearWage, RIGHT('0' + CAST(WG.MonthWage AS VARCHAR(2)), 2)) AS ProcMonth, 
WG.AadharNo 
,WG.VendorCode,
WG.VendorName,
WG.WorkOrderNo,
WG.LocationCode,
WG.LocationNM,
WG.WorkManCategory,
(select top 1 GatePass_No from App_Online_Gatepass_Details where v_code=WG.VendorCode AND Addhar=WG.AadharNo  order by CreatedOn desc) as GatePassNo,
(select top 1 CreatedOn_GP from App_Online_Gatepass_Details where v_code=WG.VendorCode AND Addhar=WG.AadharNo  order by CreatedOn desc) as CreatedOn_GP,
(select top 1 GatePass_Validity from App_Online_Gatepass_Details where v_code=WG.VendorCode AND Addhar=WG.AadharNo  order by CreatedOn desc) as GatePass_Validity,
WG.TotPaymentDays, 
WG.BasicWages,
WG.DAWages,
WG.TotalWages AS GrossWage,
(select top 1 EM.Sex from App_EmployeeMaster  EM where WG.AadharNo = EM.AadharCard AND WG.VendorCode = EM.VendorCode order by CreatedOn desc) sex ,
(select DEPT_CODE from App_WorkOrder_Reg where WO_NO=WG.WorkOrderNo) as department, WG.StateName
FROM App_WagesDetailsJharkhand WG 
WHERE WG.StateName = 'Jharkhand'   
