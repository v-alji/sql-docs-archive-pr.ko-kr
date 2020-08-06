---
title: CLR 트리거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- inserted tables
- database objects [CLR integration], triggers
- common language runtime [SQL Server], triggers
- updated columns
- building database objects [CLR integration], triggers
- triggers [CLR integration]
- deleted tables
- EventData property
- SqlTriggerContext class
- transactions [CLR integration]
ms.assetid: 302a4e4a-3172-42b6-9cc0-4a971ab49c1c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 91f12b0d97d2e2065c5bb08d175253c22dffb032
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648534"
---
# <a name="clr-triggers"></a><span data-ttu-id="54dee-102">CLR 트리거</span><span class="sxs-lookup"><span data-stu-id="54dee-102">CLR Triggers</span></span>
  <span data-ttu-id="54dee-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR(공용 언어 런타임)과의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 통합으로 인해 모든 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 언어를 사용하여 CLR 트리거를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-103">Because of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR), you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language to create CLR triggers.</span></span> <span data-ttu-id="54dee-104">이 섹션에서는 CLR 통합을 사용하여 구현된 트리거와 관련된 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-104">This section covers information specific to triggers implemented with CLR integration.</span></span> <span data-ttu-id="54dee-105">트리거에 대 한 자세한 설명은 [DDL 트리거](../../relational-databases/triggers/ddl-triggers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54dee-105">For a complete discussion of triggers, see [DDL Triggers](../../relational-databases/triggers/ddl-triggers.md).</span></span>  
  
## <a name="what-are-triggers"></a><span data-ttu-id="54dee-106">트리거란?</span><span class="sxs-lookup"><span data-stu-id="54dee-106">What Are Triggers?</span></span>  
 <span data-ttu-id="54dee-107">트리거는 언어 이벤트가 실행될 때 자동으로 실행되는 특별한 유형의 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-107">A trigger is a special type of stored procedure that automatically runs when a language event executes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="54dee-108">에는 DML (데이터 조작 언어) 및 DDL (데이터 정의 언어) 트리거와 같은 두 가지 일반적인 유형의 트리거가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-108">includes two general types of triggers: data manipulation language (DML) and data definition language (DDL) triggers.</span></span> <span data-ttu-id="54dee-109">DML 트리거는 `INSERT`, `UPDATE` 또는 `DELETE` 문이 지정된 테이블 또는 뷰의 데이터를 수정할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-109">DML triggers can be used when `INSERT`, `UPDATE`, or `DELETE` statements modify data in a specified table or view.</span></span> <span data-ttu-id="54dee-110">DDL 트리거는 주로 `CREATE`, `ALTER` 및 `DROP`으로 시작하는 문인 다양한 DDL 문에 대한 응답으로 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-110">DDL triggers fire stored procedures in response to a variety of DDL statements, which are primarily statements that begin with `CREATE`, `ALTER`, and `DROP`.</span></span> <span data-ttu-id="54dee-111">데이터베이스 작업 감사 및 조정 등의 관리 태스크에 DDL 트리거를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-111">DDL triggers can be used for administrative tasks, such as auditing and regulating database operations.</span></span>  
  
## <a name="unique-capabilities-of-clr-triggers"></a><span data-ttu-id="54dee-112">CLR 트리거의 고유한 기능</span><span class="sxs-lookup"><span data-stu-id="54dee-112">Unique Capabilities of CLR Triggers</span></span>  
 <span data-ttu-id="54dee-113">[!INCLUDE[tsql](../../includes/tsql-md.md)]로 작성된 트리거에는 `UPDATE(column)` 및 `COLUMNS_UPDATED()` 함수를 사용하여 업데이트된 발생 뷰 또는 테이블의 열을 확인하는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-113">Triggers written in [!INCLUDE[tsql](../../includes/tsql-md.md)] have the capability of determining which columns from the firing view or table have been updated by using the `UPDATE(column)` and `COLUMNS_UPDATED()` functions.</span></span>  
  
 <span data-ttu-id="54dee-114">CLR 언어로 작성된 트리거는 몇 가지 중요한 방식에서 다른 CLR 통합 개체와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-114">Triggers written in a CLR language differ from other CLR integration objects in several significant ways.</span></span> <span data-ttu-id="54dee-115">CLR 트리거는 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-115">CLR triggers can:</span></span>  
  
-   <span data-ttu-id="54dee-116">`INSERTED` 및 `DELETED` 테이블의 데이터 참조</span><span class="sxs-lookup"><span data-stu-id="54dee-116">Reference data in the `INSERTED` and `DELETED` tables</span></span>  
  
-   <span data-ttu-id="54dee-117">`UPDATE` 작업의 결과로 수정된 열 확인</span><span class="sxs-lookup"><span data-stu-id="54dee-117">Determine which columns have been modified as a result of an `UPDATE` operation</span></span>  
  
-   <span data-ttu-id="54dee-118">DDL 문 실행의 영향을 받는 데이터베이스 개체에 대한 정보 액세스</span><span class="sxs-lookup"><span data-stu-id="54dee-118">Access information about database objects affected by the execution of DDL statements.</span></span>  
  
 <span data-ttu-id="54dee-119">이러한 기능은 쿼리 언어에서 기본적으로 또는 `SqlTriggerContext` 클래스에 의해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-119">These capabilities are provided inherently in the query language, or by the `SqlTriggerContext` class.</span></span> <span data-ttu-id="54dee-120">CLR 통합의 장점 및 관리 코드와 관리 코드를 선택 하는 방법에 대 한 자세한 내용은 [!INCLUDE[tsql](../../includes/tsql-md.md)] [Clr 통합 개요](../../relational-databases/clr-integration/clr-integration-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54dee-120">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="using-the-sqltriggercontext-class"></a><span data-ttu-id="54dee-121">SqlTriggerContext 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="54dee-121">Using the SqlTriggerContext Class</span></span>  
 <span data-ttu-id="54dee-122">`SqlTriggerContext` 클래스는 공개적으로 생성할 수 없으며, CLR 트리거 본문 내에서 `SqlContext.TriggerContext` 속성에 액세스해야만 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-122">The `SqlTriggerContext` class cannot be publicly constructed and can only be obtained by accessing the `SqlContext.TriggerContext` property within the body of a CLR trigger.</span></span> <span data-ttu-id="54dee-123">`SqlTriggerContext` 클래스는 `SqlContext` 속성을 호출하여 활성 `SqlContext.TriggerContext`에서 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-123">The `SqlTriggerContext` class can be obtained from the active `SqlContext` by calling the `SqlContext.TriggerContext` property:</span></span>  
  
 `SqlTriggerContext myTriggerContext = SqlContext.TriggerContext;`  
  
 <span data-ttu-id="54dee-124">`SqlTriggerContext` 클래스는 트리거에 대한 컨텍스트 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-124">The `SqlTriggerContext` class provides context information about the trigger.</span></span> <span data-ttu-id="54dee-125">이 컨텍스트 정보에는 트리거를 발생시킨 동작 유형, UPDATE 작업에서 수정된 열, DDL 트리거의 경우 트리거 작업을 설명하는 `EventData` 구조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-125">This contextual information includes the type of action that caused the trigger to fire, which columns were modified in an UPDATE operation, and, in the case of a DDL trigger, an XML `EventData` structure which describes the triggering operation.</span></span> <span data-ttu-id="54dee-126">자세한 내용은 [EVENTDATA &#40;transact-sql&#41;](/sql/t-sql/functions/eventdata-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54dee-126">For more information, see [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).</span></span>  
  
### <a name="determining-the-trigger-action"></a><span data-ttu-id="54dee-127">트리거 동작 확인</span><span class="sxs-lookup"><span data-stu-id="54dee-127">Determining the Trigger Action</span></span>  
 <span data-ttu-id="54dee-128">`SqlTriggerContext`를 얻은 후 트리거를 발생시킨 동작 유형을 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-128">Once you have obtained a `SqlTriggerContext`, you can use it to determine the type of action that caused the trigger to fire.</span></span> <span data-ttu-id="54dee-129">이 정보는 `TriggerAction` 클래스의 `SqlTriggerContext` 속성을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-129">This information is available through the `TriggerAction` property of the `SqlTriggerContext` class.</span></span>  
  
 <span data-ttu-id="54dee-130">DML 트리거의 경우 `TriggerAction` 속성은 다음 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-130">For DML triggers, the `TriggerAction` property can be one of the following values:</span></span>  
  
-   <span data-ttu-id="54dee-131">TriggerAction.Update (0x1)</span><span class="sxs-lookup"><span data-stu-id="54dee-131">TriggerAction.Update (0x1)</span></span>  
  
-   <span data-ttu-id="54dee-132">TriggerAction.Insert (0x2)</span><span class="sxs-lookup"><span data-stu-id="54dee-132">TriggerAction.Insert (0x2)</span></span>  
  
-   <span data-ttu-id="54dee-133">TriggerAction.Delete(0x3)</span><span class="sxs-lookup"><span data-stu-id="54dee-133">TriggerAction.Delete(0x3)</span></span>  
  
-   <span data-ttu-id="54dee-134">DDL 트리거의 경우 가능한 TriggerAction 값의 목록이 훨씬 더 깁니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-134">For DDL triggers, the list of possible TriggerAction values is considerably longer.</span></span> <span data-ttu-id="54dee-135">자세한 내용은 .NET Framework SDK의 "TriggerAction 열거형"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="54dee-135">Please see "TriggerAction Enumeration" in the .NET Framework SDK for more information.</span></span>  
  
### <a name="using-the-inserted-and-deleted-tables"></a><span data-ttu-id="54dee-136">Inserted 및 Deleted 테이블 사용</span><span class="sxs-lookup"><span data-stu-id="54dee-136">Using the Inserted and Deleted Tables</span></span>  
 <span data-ttu-id="54dee-137">DML 트리거 문에는 **inserted** 테이블과 **deleted** 테이블 이라는 두 개의 특수 테이블이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-137">Two special tables are used in DML trigger statements: the **inserted** table and the **deleted** table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="54dee-138">에서는 이러한 테이블을 자동으로 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-138">automatically creates and manages these tables.</span></span> <span data-ttu-id="54dee-139">이러한 임시 테이블을 사용하여 특정 데이터의 수정 결과를 테스트하고 DML 트리거 동작에 대한 조건을 설정할 수 있습니다. 하지만 테이블의 데이터를 직접 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-139">You can use these temporary tables to test the effects of certain data modifications and to set conditions for DML trigger actions; however, you cannot alter the data in the tables directly.</span></span>  
  
 <span data-ttu-id="54dee-140">CLR 트리거는 CLR in-process 공급자를 통해 **inserted** 및 **deleted** 테이블에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-140">CLR triggers can access the **inserted** and **deleted** tables through the CLR in-process provider.</span></span> <span data-ttu-id="54dee-141">이 작업을 수행하려면 SqlContext 개체에서 `SqlCommand` 개체를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-141">This is done by obtaining a `SqlCommand` object from the SqlContext object.</span></span> <span data-ttu-id="54dee-142">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-142">For example:</span></span>  
  
 <span data-ttu-id="54dee-143">C#</span><span class="sxs-lookup"><span data-stu-id="54dee-143">C#</span></span>  
  
```  
SqlConnection connection = new SqlConnection ("context connection = true");  
connection.Open();  
SqlCommand command = connection.CreateCommand();  
command.CommandText = "SELECT * from " + "inserted";  
```  
  
 <span data-ttu-id="54dee-144">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54dee-144">Visual Basic</span></span>  
  
```  
Dim connection As New SqlConnection("context connection=true")  
Dim command As SqlCommand  
connection.Open()  
command = connection.CreateCommand()  
command.CommandText = "SELECT * FROM " + "inserted"  
```  
  
### <a name="determining-updated-columns"></a><span data-ttu-id="54dee-145">업데이트된 열 확인</span><span class="sxs-lookup"><span data-stu-id="54dee-145">Determining Updated Columns</span></span>  
 <span data-ttu-id="54dee-146">`ColumnCount` 개체의 `SqlTriggerContext` 속성을 사용하여 UPDATE 작업에서 수정된 열 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-146">You can determine the number of columns that were modified by an UPDATE operation by using the `ColumnCount` property of the `SqlTriggerContext` object.</span></span> <span data-ttu-id="54dee-147">열 서수를 입력 매개 변수로 사용하는 `IsUpdatedColumn` 메서드를 사용하여 열이 업데이트되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-147">You can use the `IsUpdatedColumn` method, which takes the column ordinal as an input parameter, to determine whether the column was updated.</span></span> <span data-ttu-id="54dee-148">`True` 값은 열이 업데이트되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-148">A `True` value indicates that the column has been updated.</span></span>  
  
 <span data-ttu-id="54dee-149">예를 들어 이 항목의 뒷부분에 있는 EmailAudit 트리거에서 가져온 다음 코드 조각은 업데이트된 모든 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-149">For example, this code snippet (from the EmailAudit trigger later in this topic) lists all of the columns updated:</span></span>  
  
 <span data-ttu-id="54dee-150">C#</span><span class="sxs-lookup"><span data-stu-id="54dee-150">C#</span></span>  
  
```  
reader = command.ExecuteReader();  
reader.Read();  
for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
{  
   pipe.Send("Updated column "  
      + reader.GetName(columnNumber) + "? "  
   + triggContext.IsUpdatedColumn(columnNumber).ToString());  
 }  
  
 reader.Close();  
```  
  
 <span data-ttu-id="54dee-151">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54dee-151">Visual Basic</span></span>  
  
```  
reader = command.ExecuteReader()  
reader.Read()  
Dim columnNumber As Integer  
  
For columnNumber=0 To triggContext.ColumnCount-1  
  
   pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
   "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
Next  
  
reader.Close()  
```  
  
### <a name="accessing-eventdata-for-clr-ddl-triggers"></a><span data-ttu-id="54dee-152">CLR DDL 트리거에 대한 EventData 액세스</span><span class="sxs-lookup"><span data-stu-id="54dee-152">Accessing EventData for CLR DDL Triggers</span></span>  
 <span data-ttu-id="54dee-153">DDL 트리거는 일반 트리거와 마찬가지로 이벤트에 응답하여 저장 프로시저를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-153">DDL triggers, like regular triggers, fire stored procedures in response to an event.</span></span> <span data-ttu-id="54dee-154">그러나 DML 트리거와 달리 DDL 트리거는 테이블이나 뷰에서 UPDATE, INSERT 또는 DELETE 문에 응답하여 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-154">But unlike DML triggers, they do not fire in response to UPDATE, INSERT, or DELETE statements on a table or view.</span></span> <span data-ttu-id="54dee-155">대신 DDL 트리거는 주로 CREATE, ALTER 및 DROP으로 시작하는 문인 다양한 DDL 문에 대한 응답으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-155">Instead, they fire in response to a variety of DDL statements, which are primarily statements that begin with CREATE, ALTER, and DROP.</span></span> <span data-ttu-id="54dee-156">데이터베이스 작업과 스키마 변경 내용 감사 및 모니터링과 같은 관리 태스크에 DDL 트리거를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-156">DDL triggers can be used for administrative tasks, such as auditing and monitoring of database operations and schema changes.</span></span>  
  
 <span data-ttu-id="54dee-157">DDL 트리거를 발생시키는 이벤트에 대한 정보는 `EventData` 클래스의 `SqlTriggerContext` 속성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-157">Information about an event that fires a DDL trigger is available in the `EventData` property of the `SqlTriggerContext` class.</span></span> <span data-ttu-id="54dee-158">이 속성에는 `xml` 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-158">This property contains an `xml` value.</span></span> <span data-ttu-id="54dee-159">xml 스키마에는 다음에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-159">The xml schema includes information about:</span></span>  
  
-   <span data-ttu-id="54dee-160">이벤트의 시간</span><span class="sxs-lookup"><span data-stu-id="54dee-160">The time of the event.</span></span>  
  
-   <span data-ttu-id="54dee-161">트리거가 실행된 동안의 연결 SPID(시스템 프로세스 ID)</span><span class="sxs-lookup"><span data-stu-id="54dee-161">The System Process ID (SPID) of the connection during which the trigger executed.</span></span>  
  
-   <span data-ttu-id="54dee-162">트리거를 실행한 이벤트의 유형</span><span class="sxs-lookup"><span data-stu-id="54dee-162">The type of event that fired the trigger.</span></span>  
  
 <span data-ttu-id="54dee-163">그런 다음 이벤트 유형에 따라 스키마에 이벤트가 발생한 데이터베이스, 이벤트가 발생한 개체 및 이벤트의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령과 같은 추가 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-163">Then, depending on the event type, the schema includes additional information, such as the database in which the event occurred, the object against which the event occurred, and the [!INCLUDE[tsql](../../includes/tsql-md.md)] command of the event.</span></span>  
  
 <span data-ttu-id="54dee-164">다음 예에서 DDL 트리거는 원시 `EventData` 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-164">In the following example, the following DDL trigger returns the raw `EventData` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54dee-165">여기에 표시된 `SqlPipe` 개체를 통한 결과 및 메시지 전송은 설명 목적으로만 제공되며, 일반적으로 CLR 트리거를 프로그래밍할 때 프로덕션 코드에 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-165">Sending results and messages through the `SqlPipe` object is shown here for illustrative purposes only and is generally discouraged for production code when programming CLR triggers.</span></span> <span data-ttu-id="54dee-166">예기치 않은 추가 데이터가 반환되고 애플리케이션 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-166">Additional data returned may be unexpected and lead to application errors.</span></span>  
  
 <span data-ttu-id="54dee-167">C#</span><span class="sxs-lookup"><span data-stu-id="54dee-167">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   public static void DropTableTrigger()  
   {  
       SqlTriggerContext triggContext = SqlContext.TriggerContext;             
  
       switch(triggContext.TriggerAction)  
       {  
           case TriggerAction.DropTable:  
           SqlContext.Pipe.Send("Table dropped! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
  
           default:  
           SqlContext.Pipe.Send("Something happened! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
       }  
   }  
}  
```  
  
 <span data-ttu-id="54dee-168">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54dee-168">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    Public Shared Sub DropTableTrigger()  
        Dim triggContext As SqlTriggerContext  
        triggContext = SqlContext.TriggerContext  
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.DropTable  
              SqlContext.Pipe.Send("Table dropped! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
           Case Else  
              SqlContext.Pipe.Send("Something else happened! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
        End Select  
    End Sub  
End Class     
```  
  
 <span data-ttu-id="54dee-169">다음 예제 출력은 `EventData` 이벤트에 의해 DDL 트리거가 발생한 후의 `CREATE TABLE` 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-169">The following sample output is the `EventData` property value after a DDL trigger fired by a `CREATE TABLE` event:</span></span>  
  
 `<EVENT_INSTANCE><PostTime>2004-04-16T21:17:16.160</PostTime><SPID>58</SPID><EventType>CREATE_TABLE</EventType><ServerName>MACHINENAME</ServerName><LoginName>MYDOMAIN\myname</LoginName><UserName>MYDOMAIN\myname</UserName><DatabaseName>AdventureWorks</DatabaseName><SchemaName>dbo</SchemaName><ObjectName>UserName</ObjectName><ObjectType>TABLE</ObjectType><TSQLCommand><SetOptions ANSI_NULLS="ON" ANSI_NULL_DEFAULT="ON" ANSI_PADDING="ON" QUOTED_IDENTIFIER="ON" ENCRYPTED="FALSE" /><CommandText>create table dbo.UserName  
(  
 UserName varchar(50),  
 RealName varchar(50)  
)  
</CommandText></TSQLCommand></EVENT_INSTANCE>`  
  
 <span data-ttu-id="54dee-170">`SqlTriggerContext` 클래스를 통해 액세스할 수 있는 정보 외에도 쿼리는 in-process 실행된 명령의 텍스트 내에서 `COLUMNS_UPDATED` 및 inserted/deleted를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-170">In addition to the information accessible through the `SqlTriggerContext` class, queries can still refer to `COLUMNS_UPDATED` and inserted/deleted within the text of a command executed in-process.</span></span>  
  
## <a name="sample-clr-trigger"></a><span data-ttu-id="54dee-171">예제 CLR 트리거</span><span class="sxs-lookup"><span data-stu-id="54dee-171">Sample CLR Trigger</span></span>  
 <span data-ttu-id="54dee-172">이 예에서 사용자가 원하는 ID를 선택할 수 있도록 하지만 구체적으로 전자 메일 주소를 ID로 입력한 사용자를 확인하려는 시나리오를 살펴 보십시오.</span><span class="sxs-lookup"><span data-stu-id="54dee-172">In this example, consider the scenario in which you let the user choose any ID they want, but you want to know the users that specifically entered an e-mail address as an ID.</span></span> <span data-ttu-id="54dee-173">다음 트리거는 해당 정보를 검색하여 감사 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-173">The following trigger would detect that information and log it to an audit table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54dee-174">여기에 표시된 `SqlPipe` 개체를 통한 결과 및 메시지 전송은 설명 목적으로만 제공되며, 일반적으로 프로덕션 코드에 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-174">Sending results and messages through the `SqlPipe` object is shown here for illustrative purposes only and is generally discouraged for production code.</span></span> <span data-ttu-id="54dee-175">예기치 않은 추가 데이터가 반환되고 애플리케이션 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-175">Additional data returned may be unexpected and lead to application errors</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   [SqlTrigger(Name = @"EmailAudit", Target = "[dbo].[Users]", Event = "FOR INSERT, UPDATE, DELETE")]  
   public static void EmailAudit()  
   {  
      string userName;  
      string realName;  
      SqlCommand command;  
      SqlTriggerContext triggContext = SqlContext.TriggerContext;  
      SqlPipe pipe = SqlContext.Pipe;  
      SqlDataReader reader;  
  
      switch (triggContext.TriggerAction)  
      {  
         case TriggerAction.Insert:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
            reader.Close();  
  
            if (IsValidEMailAddress(userName))  
            {  
               command = new SqlCommand(  
                  @"INSERT [dbo].[UserNameAudit] VALUES ('"  
                  + userName + @"', '" + realName + @"');",  
                  connection);  
               pipe.Send(command.CommandText);  
               command.ExecuteNonQuery();  
               pipe.Send("You inserted: " + userName);  
            }  
         }  
  
         break;  
  
         case TriggerAction.Update:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
  
            pipe.Send(@"You updated: '" + userName + @"' - '"  
               + realName + @"'");  
  
            for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
            {  
               pipe.Send("Updated column "  
                  + reader.GetName(columnNumber) + "? "  
                  + triggContext.IsUpdatedColumn(columnNumber).ToString());  
            }  
  
            reader.Close();  
         }  
  
         break;  
  
         case TriggerAction.Delete:  
            using (SqlConnection connection  
               = new SqlConnection(@"context connection=true"))  
               {  
                  connection.Open();  
                  command = new SqlCommand(@"SELECT * FROM DELETED;",  
                     connection);  
                  reader = command.ExecuteReader();  
  
                  if (reader.HasRows)  
                  {  
                     pipe.Send(@"You deleted the following rows:");  
                     while (reader.Read())  
                     {  
                        pipe.Send(@"'" + reader.GetString(0)  
                        + @"', '" + reader.GetString(1) + @"'");  
                     }  
  
                     reader.Close();  
  
                     //alternately, to just send a tabular resultset back:  
                     //pipe.ExecuteAndSend(command);  
                  }  
                  else  
                  {  
                     pipe.Send("No rows affected.");  
                  }  
               }  
  
               break;  
            }  
        }  
  
     public static bool IsValidEMailAddress(string email)  
     {  
         return Regex.IsMatch(email, @"^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$");  
     }  
}  
```  
  
 <span data-ttu-id="54dee-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54dee-176">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Text.RegularExpressions  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    <SqlTrigger(Name:="EmailAudit", Target:="[dbo].[Users]", Event:="FOR INSERT, UPDATE, DELETE")> _  
    Public Shared Sub EmailAudit()  
        Dim userName As String  
        Dim realName As String  
        Dim command As SqlCommand  
        Dim triggContext As SqlTriggerContext  
        Dim pipe As SqlPipe  
        Dim reader As SqlDataReader    
  
        triggContext = SqlContext.TriggerContext      
        pipe = SqlContext.Pipe    
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.Insert  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 reader.Close()  
  
                 If IsValidEmailAddress(userName) Then  
                     command = New SqlCommand("INSERT [dbo].[UserNameAudit] VALUES ('" & _  
                       userName & "', '" & realName & "');", connection)  
  
                    pipe.Send(command.CommandText)  
                    command.ExecuteNonQuery()  
                    pipe.Send("You inserted: " & userName)  
  
                 End If  
              End Using  
  
           Case TriggerAction.Update  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 pipe.Send("You updated: " & userName & " - " & realName)  
  
                 Dim columnNumber As Integer  
  
                 For columnNumber=0 To triggContext.ColumnCount-1  
  
                    pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
                      "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
                 Next  
  
                 reader.Close()  
              End Using  
  
           Case TriggerAction.Delete  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM DELETED;", connection)  
  
                 reader = command.ExecuteReader()  
  
                 If reader.HasRows Then  
                    pipe.Send("You deleted the following rows:")  
  
                    While reader.Read()  
  
                       pipe.Send( reader.GetString(0) & ", " & reader.GetString(1) )  
  
                    End While   
  
                    reader.Close()  
  
                    ' Alternately, just send a tabular resultset back:  
                    ' pipe.ExecuteAndSend(command)  
  
                 Else  
                   pipe.Send("No rows affected.")  
                 End If  
  
              End Using   
        End Select  
    End Sub  
  
    Public Shared Function IsValidEMailAddress(emailAddress As String) As Boolean  
  
       return Regex.IsMatch(emailAddress, "^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$")  
    End Function      
End Class  
```  
  
 <span data-ttu-id="54dee-177">다음과 같이 정의된 두 테이블이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-177">Assuming two tables exist with the following definitions:</span></span>  
  
```  
CREATE TABLE Users  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
);  
GO CREATE TABLE UserNameAudit  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
)  
```  
  
 <span data-ttu-id="54dee-178">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 트리거를 만드는 문은 다음과 같습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .에서는 현재 데이터베이스에 **sqlclrtest** 어셈블리가 이미 등록 되어 있다고 가정 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="54dee-178">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates the trigger in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is as follows, and assumes assembly **SQLCLRTest** is already registered in the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
```  
CREATE TRIGGER EmailAudit  
ON Users  
FOR INSERT, UPDATE, DELETE  
AS  
EXTERNAL NAME SQLCLRTest.CLRTriggers.EmailAudit  
```  
  
## <a name="validating-and-canceling-invalid-transactions"></a><span data-ttu-id="54dee-179">잘못된 트랜잭션 유효성 검사 및 취소</span><span class="sxs-lookup"><span data-stu-id="54dee-179">Validating and Canceling Invalid Transactions</span></span>  
 <span data-ttu-id="54dee-180">일반적으로 트리거를 사용하여 잘못된 INSERT, UPDATE 또는 DELETE 트랜잭션의 유효성을 검사하고 취소하거나 데이터베이스 스키마 변경을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-180">Using triggers to validate and cancel invalid INSERT, UPDATE, or DELETE transactions or to prevent changes to your database schema is common.</span></span> <span data-ttu-id="54dee-181">이 작업을 수행하려면 유효성 검사 논리를 트리거에 통합한 다음 동작이 유효성 조건을 충족하지 않을 경우 현재 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-181">This can be accomplished by incorporating validation logic into your trigger and then rolling back the current transaction if the action does not meet the validation criteria.</span></span>  
  
 <span data-ttu-id="54dee-182">트리거 내에서 호출할 경우 `Transaction.Rollback` 메서드 또는 명령 텍스트 "TRANSACTION ROLLBACK"을 사용한 SqlCommand는 모호한 오류 메시지로 예외를 throw하고 try/catch 블록에 래핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-182">When called within a trigger, the `Transaction.Rollback` method or a SqlCommand with the command text "TRANSACTION ROLLBACK" throws an exception with an ambiguous error message and must be wrapped in a try/catch block.</span></span> <span data-ttu-id="54dee-183">표시되는 오류 메시지는 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-183">The error message you see is similar to the following:</span></span>  
  
```  
Msg 6549, Level 16, State 1, Procedure trig_InsertValidator, Line 0  
A .NET Framework error occurred during execution of user defined routine or aggregate 'trig_InsertValidator':   
System.Data.SqlClient.SqlException: Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting... User transaction, if any, will be rolled back.  
```  
  
 <span data-ttu-id="54dee-184">이 예외는 예상된 것이며, 코드 실행을 계속하려면 try/catch 블록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-184">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="54dee-185">트리거 코드 실행이 완료되면 다른 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-185">When the trigger code finishes execution, another exception is raised</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure trig_InsertValidator, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate "trig_InsertValidator" has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting.  
The statement has been terminated.  
```  
  
 <span data-ttu-id="54dee-186">이 예외도 예상된 것이며, 실행을 계속하려면 트리거를 발생시키는 동작을 수행하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 try/catch 블록으로 둘러싸여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-186">This exception is also expected, and a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger is necessary so that execution can continue.</span></span> <span data-ttu-id="54dee-187">두 가지 예외가 throw되지만 트랜잭션이 롤백되고 변경 내용이 테이블에 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-187">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed to the table.</span></span> <span data-ttu-id="54dee-188">CLR 트리거와 [!INCLUDE[tsql](../../includes/tsql-md.md)] 트리거 사이의 주요 차이점은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 트리거의 경우 트랜잭션이 롤백된 후 계속 추가 작업을 수행할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-188">A major difference between CLR triggers and [!INCLUDE[tsql](../../includes/tsql-md.md)] triggers is that [!INCLUDE[tsql](../../includes/tsql-md.md)] triggers can continue to perform more work after the transaction is rolled back.</span></span>  
  
### <a name="example"></a><span data-ttu-id="54dee-189">예제</span><span class="sxs-lookup"><span data-stu-id="54dee-189">Example</span></span>  
 <span data-ttu-id="54dee-190">다음 트리거는 테이블의 INSERT 문에 대해 간단한 유효성 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-190">The following trigger performs simple validation of INSERT statements on a table.</span></span> <span data-ttu-id="54dee-191">삽입된 정수 값이 1이면 트랜잭션이 롤백되고 값이 테이블에 삽입되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-191">If the inserted integer value is equal to one, the transaction is rolled back and the value is not inserted into the table.</span></span> <span data-ttu-id="54dee-192">다른 모든 정수 값은 테이블에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-192">All other integer values are inserted into the table.</span></span> <span data-ttu-id="54dee-193">`Transaction.Rollback` 메서드를 둘러싼 try/catch 블록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-193">Note the try/catch block around the `Transaction.Rollback` method.</span></span> <span data-ttu-id="54dee-194">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트는 테스트 테이블, 어셈블리 및 관리되는 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-194">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates a test table, assembly, and managed stored procedure.</span></span> <span data-ttu-id="54dee-195">트리거 실행을 완료할 때 throw되는 예외가 catch되도록 두 개의 INSERT 문이 try/catch 블록에 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="54dee-195">Note that the two INSERT statements are wrapped in a try/catch block so that the exception thrown when the trigger finishes execution is caught.</span></span>  
  
 <span data-ttu-id="54dee-196">C#</span><span class="sxs-lookup"><span data-stu-id="54dee-196">C#</span></span>  
  
```  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class Triggers  
{  
    // Enter existing table or view for the target and uncomment the attribute line  
    // [Microsoft.SqlServer.Server.SqlTrigger (Name="trig_InsertValidator", Target="Table1", Event="FOR INSERT")]  
    public static void trig_InsertValidator()  
    {  
        using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
        {  
            SqlCommand command;  
            SqlDataReader reader;  
            int value;  
  
            // Open the connection.  
            connection.Open();  
  
            // Get the inserted value.  
            command = new SqlCommand(@"SELECT * FROM INSERTED", connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            value = (int)reader[0];  
            reader.Close();  
  
            // Rollback the transaction if a value of 1 was inserted.  
            if (1 == value)  
            {  
                try  
                {  
                    // Get the current transaction and roll it back.  
                    Transaction trans = Transaction.Current;  
                    trans.Rollback();                      
                }  
                catch (SqlException ex)  
                {  
                    // Catch the expected exception.                      
                }  
            }  
            else  
            {  
                // Perform other actions here.  
            }  
  
            // Close the connection.  
            connection.Close();              
        }  
    }  
}  
```  
  
 <span data-ttu-id="54dee-197">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54dee-197">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class Triggers  
' Enter existing table or view for the target and uncomment the attribute line  
' <Microsoft.SqlServer.Server.SqlTrigger(Name:="trig_InsertValidator", Target:="Table1", Event:="FOR INSERT")> _  
Public Shared Sub  trig_InsertValidator ()  
    Using connection As New SqlConnection("context connection=true")  
  
        Dim command As SqlCommand  
        Dim reader As SqlDataReader  
        Dim value As Integer  
  
        ' Open the connection.  
        connection.Open()  
  
        ' Get the inserted value.  
        command = New SqlCommand("SELECT * FROM INSERTED", connection)  
        reader = command.ExecuteReader()  
        reader.Read()  
        value = CType(reader(0), Integer)  
        reader.Close()  
  
        ' Rollback the transaction if a value of 1 was inserted.  
        If value = 1 Then  
  
            Try  
                ' Get the current transaction and roll it back.  
                Dim trans As Transaction  
                trans = Transaction.Current  
                trans.Rollback()  
  
            Catch ex As SqlException  
  
                ' Catch the exception.                      
            End Try  
        Else  
  
            ' Perform other actions here.  
        End If  
  
        ' Close the connection.  
        connection.Close()  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="54dee-198">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="54dee-198">Transact-SQL</span></span>  
  
```  
-- Create the test table, assembly, and trigger.  
CREATE TABLE Table1(c1 int);  
go  
  
CREATE ASSEMBLY ValidationTriggers from 'E:\programming\ ValidationTriggers.dll';  
go  
  
CREATE TRIGGER trig_InsertValidator  
ON Table1  
FOR INSERT  
AS EXTERNAL NAME ValidationTriggers.Triggers.trig_InsertValidator;  
go  
  
-- Use a Try/Catch block to catch the expected exception  
BEGIN TRY  
   INSERT INTO Table1 VALUES(42)  
   INSERT INTO Table1 VALUES(1)  
END TRY  
BEGIN CATCH  
  SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
END CATCH;  
  
-- Clean up.  
DROP TRIGGER trig_InsertValidator;  
DROP ASSEMBLY ValidationTriggers;  
DROP TABLE Table1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="54dee-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54dee-199">See Also</span></span>  
 <span data-ttu-id="54dee-200">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54dee-200">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="54dee-201">[DML 트리거](../../relational-databases/triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="54dee-201">[DML Triggers](../../relational-databases/triggers/dml-triggers.md) </span></span>  
 <span data-ttu-id="54dee-202">[DDL 트리거](../../relational-databases/triggers/ddl-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="54dee-202">[DDL Triggers](../../relational-databases/triggers/ddl-triggers.md) </span></span>  
 <span data-ttu-id="54dee-203">[TRY...CATCH&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54dee-203">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="54dee-204">[CLR&#41; 통합 &#40;공용 언어 런타임을 사용 하 여 데이터베이스 개체 빌드](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md) </span><span class="sxs-lookup"><span data-stu-id="54dee-204">[Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md) </span></span>  
 [<span data-ttu-id="54dee-205">EVENTDATA&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="54dee-205">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
