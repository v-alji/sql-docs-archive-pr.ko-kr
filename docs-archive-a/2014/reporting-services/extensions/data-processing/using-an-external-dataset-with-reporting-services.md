---
title: Reporting Services에서 외부 데이터 세트 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- DataSet objects [Reporting Services]
- data processing extensions [Reporting Services], custom DataSet objects
- custom DataSet objects [Reporting Services]
- external DataSet objects [Reporting Services]
ms.assetid: 11daa013-ec17-4760-80e3-6d84cd8d5722
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f41ba4461386e235cefe66819318106d0e72904
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741576"
---
# <a name="using-an-external-dataset-with-reporting-services"></a><span data-ttu-id="ea1ca-102">Reporting Services에서 외부 데이터 세트 사용</span><span class="sxs-lookup"><span data-stu-id="ea1ca-102">Using an External Dataset with Reporting Services</span></span>
  <span data-ttu-id="ea1ca-103">**DataSet** 개체는 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]에서 연결이 끊긴 분산 데이터 시나리오를 지원하는 데 있어 핵심적인 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-103">The **DataSet** object is central to supporting disconnected, distributed data scenarios with [!INCLUDE[vstecado](../../../includes/vstecado-md.md)].</span></span> <span data-ttu-id="ea1ca-104">**DataSet** 개체는 데이터 원본과 상관없이 일관성 있는 관계형 프로그래밍 모델을 제공하는 데이터의 메모리 상주 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-104">The **DataSet** object is a memory-resident representation of data that provides a consistent relational programming model regardless of the data source.</span></span> <span data-ttu-id="ea1ca-105">다양한 데이터 원본 또는 XML 데이터와 함께 사용하거나 애플리케이션의 로컬 데이터를 관리하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-105">It can be used with multiple different data sources, with XML data, or to manage data local to the application.</span></span> <span data-ttu-id="ea1ca-106">**DataSet** 개체는 관련 테이블, 제약 조건, 테이블 간의 관계 등을 포함한 전체 데이터 세트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-106">The **DataSet** object represents a complete set of data, including related tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="ea1ca-107">**DataSet** 개체는 데이터를 유연하게 저장하고 표시할 수 있기 때문에 데이터에 대한 보고가 이루어지기 전에 데이터가 처리되고 **DataSet** 개체로 변환되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-107">Because of the **DataSet** object's versatility in storing and exposing data, your data may often be processed and transformed into a **DataSet** object before any reporting on that data occurs.</span></span>  
  
 <span data-ttu-id="ea1ca-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 사용하여 외부 애플리케이션으로 만든 사용자 지정 **DataSet** 개체를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-108">With [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extensions, you can integrate any custom **DataSet** objects that are created by external applications.</span></span> <span data-ttu-id="ea1ca-109">그러려면 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 **DataSet** 개체와 보고서 서버를 연결하는 사용자 지정 데이터 처리 확장 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-109">To accomplish this, you create a custom data processing extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] that acts like a bridge between your **DataSet** object and the report server.</span></span> <span data-ttu-id="ea1ca-110">이 **DataSet** 개체를 처리하기 위한 코드의 대부분은 사용자가 만드는 **DataReader** 클래스에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-110">Most of the code for processing this **DataSet** object is contained in the **DataReader** class that you create.</span></span>  
  
 <span data-ttu-id="ea1ca-111">**DataSet** 개체를 보고서 서버에 표시하는 첫 단계는 **DataReader** 클래스에서 **DataSet** 개체를 채울 수 있는 공급자별 메서드를 구현하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-111">The first step in exposing your **DataSet** object to the report server is to implement a provider specific method in your **DataReader** class that can populate a **DataSet** object.</span></span> <span data-ttu-id="ea1ca-112">다음 예는 **DataReader** 클래스에서 공급자별 메서드를 사용하여 **DataSet** 개체에 정적 데이터를 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-112">The following example shows how to load static data into a **DataSet** object by using a provider-specific method in your **DataReader** class.</span></span>  
  
```vb  
'Private members of the DataReader class  
Private m_dataSet As System.Data.DataSet  
Private m_currentRow As Integer  
  
'Method to create a dataset  
Friend Sub CreateDataSet()  
   ' Create a dataset.  
   Dim ds As New System.Data.DataSet("myDataSet")  
   ' Create a data table.   
   Dim dt As New System.Data.DataTable("myTable")  
   ' Create a data column and set various properties.   
   Dim dc As New System.Data.DataColumn()  
   dc.DataType = System.Type.GetType("System.Decimal")  
   dc.AllowDBNull = False  
   dc.Caption = "Number"  
   dc.ColumnName = "Number"  
   dc.DefaultValue = 25  
   ' Add the column to the table.   
   dt.Columns.Add(dc)  
   ' Add 10 rows and set values.   
   Dim dr As System.Data.DataRow  
   Dim i As Integer  
   For i = 0 To 9  
      dr = dt.NewRow()  
      dr("Number") = i + 1  
      ' Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr)  
   Next i  
  
   ' Fill the dataset.  
   ds.Tables.Add(dt)  
  
   ' Use a private variable to store the dataset in your  
   ' DataReader.  
   m_dataSet = ds  
  
   ' Set the current row to -1.  
   m_currentRow = - 1  
End Sub 'CreateDataSet  
```  
  
```csharp  
// Private members of the DataReader class  
private System.Data.DataSet m_dataSet;  
private int m_currentRow;  
  
// Method to create a dataset  
internal void CreateDataSet()  
{  
   // Create a dataset.  
   System.Data.DataSet ds = new System.Data.DataSet("myDataSet");  
   // Create a data table.   
   System.Data.DataTable dt = new System.Data.DataTable("myTable");  
   // Create a data column and set various properties.   
   System.Data.DataColumn dc = new System.Data.DataColumn();   
   dc.DataType = System.Type.GetType("System.Decimal");   
   dc.AllowDBNull = false;   
   dc.Caption = "Number";   
   dc.ColumnName = "Number";   
   dc.DefaultValue = 25;   
   // Add the column to the table.   
   dt.Columns.Add(dc);   
   // Add 10 rows and set values.   
   System.Data.DataRow dr;   
   for(int i = 0; i < 10; i++)  
   {   
      dr = dt.NewRow();   
      dr["Number"] = i + 1;   
      // Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr);  
   }  
  
   // Fill the dataset.  
   ds.Tables.Add(dt);  
  
   // Use a private variable to store the dataset in your  
   // DataReader.  
   m_dataSet = ds;  
  
   // Set the current row to -1.  
   m_currentRow = -1;  
}  
```  
  
```csharp  
public bool Read()  
{  
   m_currentRow++;  
   if (m_currentRow >= m_dataSet.Tables[0].Rows.Count)   
   {  
      return (false);  
   }   
   else   
   {  
      return (true);  
   }  
}  
  
public int FieldCount  
{  
   // Return the count of the number of columns, which in  
   // this case is the size of the column metadata  
   // array.  
   get { return m_dataSet.Tables[0].Columns.Count; }  
}  
  
public string GetName(int i)  
{  
   return m_dataSet.Tables[0].Columns[i].ColumnName;  
}  
  
public Type GetFieldType(int i)  
{  
   // Return the actual Type class for the data type.  
   return m_dataSet.Tables[0].Columns[i].DataType;  
}  
  
public Object GetValue(int i)  
{  
   return m_dataSet.Tables[0].Rows[m_currentRow][i];  
}  
  
public int GetOrdinal(string name)  
{  
   // Look for the ordinal of the column with the same name and return it.  
   // Returns -1 if not found.  
   return m_dataSet.Tables[0].Columns[name].Ordinal;  
}  
```  
  
 <span data-ttu-id="ea1ca-113">데이터 세트를 만들거나 검색하면 **DataReader** 클래스의 **Read**, **GetValue**, **GetName**, **GetOrdinal**, **GetFieldType** 및 **FieldCount** 멤버 구현에서 **DataSet** 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ca-113">Once you create or retrieve your dataset, you can use the **DataSet** object in your implementations of the **Read**, **GetValue**, **GetName**, **GetOrdinal**, **GetFieldType**, and **FieldCount** members of the **DataReader** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1ca-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea1ca-114">See Also</span></span>  
 <span data-ttu-id="ea1ca-115">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="ea1ca-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="ea1ca-116">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ea1ca-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="ea1ca-117">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="ea1ca-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
