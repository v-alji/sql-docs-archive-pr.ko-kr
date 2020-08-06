---
title: CLR 통합 사용자 지정 특성 개요 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: aa0bf94ee27fd89a6aa690e0ff2f8e3295648946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646626"
---
# <a name="overview-of-clr-integration-custom-attributes"></a><span data-ttu-id="6a49b-102">CLR 통합 사용자 지정 특성 개요</span><span class="sxs-lookup"><span data-stu-id="6a49b-102">Overview of CLR Integration Custom Attributes</span></span>
  <span data-ttu-id="6a49b-103">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 CLR(공용 언어 런타임)에서는 특성이라고 하는 설명적 키워드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-103">The common language runtime (CLR) of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] allows the use of descriptive keywords, called attributes.</span></span> <span data-ttu-id="6a49b-104">이러한 특성은 메서드와 클래스 같은 많은 요소에 대한 추가적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-104">These attributes provide additional information for many elements, such as methods and classes.</span></span> <span data-ttu-id="6a49b-105">특성은 개체의 메타데이터와 함께 어셈블리에 저장되며 다른 개발 도구를 위한 코드 설명이나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내의 런타임 동작 제어에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-105">The attributes are saved in the assembly with the metadata of the object, and can be used to describe your code to other development tools or to affect runtime behavior inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6a49b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 CLR 루틴을 등록할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 루틴에 대한 속성 집합이 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-106">When you register a CLR routine with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives a set of properties about the routine.</span></span> <span data-ttu-id="6a49b-107">이러한 루틴 속성은 루틴에 대한 인덱싱 여부를 비롯한 루틴의 여러 가지 기능을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-107">These routine properties determine the capabilities of the routine, including whether the routine can be indexed.</span></span> <span data-ttu-id="6a49b-108">예를 들어 `DataAccess` 속성을 `DataAccessKind.Read`로 설정하면 CLR 함수 내에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 테이블의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-108">For example, setting the `DataAccess` property to `DataAccessKind.Read` lets you access data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user tables inside a CLR function.</span></span> <span data-ttu-id="6a49b-109">다음 예에서는 `DataAccess` 속성을 설정 하 여 사용자 테이블 **table1**의 데이터에 쉽게 액세스할 수 있는 간단한 사례를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-109">The following example shows a simple case in which the `DataAccess` property is set to facilitate data access from a user table **table1**.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 <span data-ttu-id="6a49b-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] 루틴의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 루틴 정의에서 직접 루틴 속성을 파생합니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-110">For [!INCLUDE[tsql](../../includes/tsql-md.md)] routines, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] derives routine properties directly from the routine definition.</span></span> <span data-ttu-id="6a49b-111">CLR 루틴의 경우에는 이러한 속성을 파생하기 위해 서버가 루틴 본문을 분석하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-111">For CLR routines, the server does not analyze the body of the routine to derive these properties.</span></span> <span data-ttu-id="6a49b-112">대신 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 언어로 구현된 클래스와 클래스 멤버의 사용자 지정 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-112">Instead, you can use custom attributes for classes and class members implemented in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language.</span></span>  
  
 <span data-ttu-id="6a49b-113">CLR 루틴, 사용자 정의 형식 및 집계에 필요한 사용자 지정 특성은 `Microsoft.SqlServer.Server` 네임스페이스에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a49b-113">The custom attributes needed for CLR routines, user-defined types, and aggregates are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a49b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a49b-114">See Also</span></span>  
 [<span data-ttu-id="6a49b-115">CLR 루틴에 대 한 사용자 지정 특성</span><span class="sxs-lookup"><span data-stu-id="6a49b-115">Custom Attributes for CLR Routines</span></span>](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  
