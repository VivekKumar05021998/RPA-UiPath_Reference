# RPA-UiPath_Reference

**#To Filter a Datatable**

outDt=(From d In dt 
Where Convert.ToString(d("Age")).Equals("299") And CInt(d("Salary"))>200000
).CopyToDataTable()

outDt=dt.Select("[Age]='23' and [Gender]='Male'").CopytoDataTable()

outDt=dt.AsEnumerable.Where(Function(x) cint(x("Salary"))>500000 AndAlso Cint(x("Age"))>20).CopytoDataTable()

outDt=if(dt.AsEnumerable.Any(Function(x) cint(x("Salary"))>5000000 AndAlso Cint(x("Age"))>20),dt.AsEnumerable.Where(Function(x) cint(x("Salary"))>500000 AndAlso Cint(x("Age"))>20).CopytoDataTable(),new DataTable)


**To Order by a datatable**

outDt=(From d In dt 
Where CInt(d("Salary"))>200000
Order By CInt(d("Salary"))
).CopyToDataTable()

outDt=dt.AsEnumerable.Where(Function(x) cint(x("Salary"))>500000 AndAlso Cint(x("Age"))>20).OrderBy(Function(y) Cint(y("Age"))).CopytoDataTable()


**GroupBy a DataTable**

outDt=(From d In dt 
Where CInt(d("Age"))>2 And CInt(d("Salary"))>20000
Group d By varAge = d("Gender").ToString Into Group
Select outDt.Rows.Add({varAge,Group.Count()})
).CopyToDataTable()
