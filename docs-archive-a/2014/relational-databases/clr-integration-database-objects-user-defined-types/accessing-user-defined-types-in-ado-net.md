---
title: ADO.NET에서 사용자 정의 형식에 액세스 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653442"
---
# <a name="accessing-user-defined-types-in-adonet"></a><span data-ttu-id="7579d-102">ADO.NET의 사용자 정의 형식 액세스</span><span class="sxs-lookup"><span data-stu-id="7579d-102">Accessing User-Defined Types in ADO.NET</span></span>
  <span data-ttu-id="7579d-103">Udt (사용자 정의 형식)는 확인할 수 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 코드를 생성 하는 .NET FRAMEWORK CLR (공용 언어 런타임)에서 지 원하는 언어를 사용 하 여 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-103">User-defined types (UDTs) are written using any of the languages supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="7579d-104">이러한 언어에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-104">This includes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic.</span></span> <span data-ttu-id="7579d-105">UDT를 사용하면 개체와 사용자 지정 데이터 구조를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-105">UDTs allow objects and custom data structures to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="7579d-106">데이터는 .NET Framework 클래스 또는 구조의 공용 멤버로 노출되며 동작은 클래스 또는 구조의 메서드로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-106">The data is exposed as public members of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span> <span data-ttu-id="7579d-107">UDT를 테이블의 열 정의, [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리의 변수 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수나 저장 프로시저의 인수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-107">A UDT can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
 <span data-ttu-id="7579d-108">ADO.NET에서 `System.Data.SqlClient` 공급자는 UDT를 다음과 같은 방식으로 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-108">In ADO.NET, the `System.Data.SqlClient` provider exposes UDTs in the following ways:</span></span>  
  
-   <span data-ttu-id="7579d-109">`System.Data.SqlClient.SqlDataReader`를 통해 개체로 노출</span><span class="sxs-lookup"><span data-stu-id="7579d-109">Through the `System.Data.SqlClient.SqlDataReader` as an object.</span></span>  
  
-   <span data-ttu-id="7579d-110">`SqlDataReader`를 통해 원시 바이트로 노출</span><span class="sxs-lookup"><span data-stu-id="7579d-110">Through the `SqlDataReader` as raw bytes.</span></span>  
  
-   <span data-ttu-id="7579d-111">`System.Data.SqlClient.SqlParameter` 개체의 매개 변수로 노출</span><span class="sxs-lookup"><span data-stu-id="7579d-111">As a parameter of a `System.Data.SqlClient.SqlParameter` object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7579d-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7579d-112">In This Section</span></span>  
 [<span data-ttu-id="7579d-113">UDT 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="7579d-113">Retrieving UDT Data</span></span>](accessing-user-defined-types-retrieving-udt-data.md)  
 <span data-ttu-id="7579d-114">UDT 데이터를 검색하는 방법과 매개 변수를 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-114">Describes how to retrieve UDT data and how to specify parameters.</span></span>  
  
 [<span data-ttu-id="7579d-115">DataAdapter로 UDT 열 업데이트</span><span class="sxs-lookup"><span data-stu-id="7579d-115">Updating UDT Columns with DataAdapters</span></span>](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 <span data-ttu-id="7579d-116">`DataSets`에서 UDT로 작업하는 방법과 `DataAdapters`를 사용하여 UDT를 업데이트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7579d-116">Describes how to work with UDTs in `DataSets` and how to update UDT data using `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7579d-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7579d-117">See Also</span></span>  
 [<span data-ttu-id="7579d-118">CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="7579d-118">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
