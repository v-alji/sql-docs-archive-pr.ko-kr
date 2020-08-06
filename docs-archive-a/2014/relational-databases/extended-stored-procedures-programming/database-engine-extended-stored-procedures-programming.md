---
title: 확장 저장 프로시저 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- gateway applications [SQL Server]
- extended stored procedures [SQL Server], about extended stored procedures
- Open Data Services [SQL Server]
- ODS [SQL Server]
ms.assetid: 561305cd-c803-48af-9eec-2c19f4d311ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 30792cc2b431e35a8f7df5ff7bbb2c228892d5c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653393"
---
# <a name="programming-extended-stored-procedures"></a><span data-ttu-id="8e2c9-102">확장 저장 프로시저 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="8e2c9-102">Programming Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="8e2c9-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="8e2c9-104">이전에는 개방형 Data Services를 사용하여 SQL Server가 아닌 데이터베이스 환경에 대한 게이트웨이와 같은 서버 애플리케이션을 작성했습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-104">In the past, Open Data Services was used to write server applications, such as gateways to non-SQL Server database environments.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="8e2c9-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 개방형 Data Services API의 사용되지 않는 부분을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support the obsolete portions of the Open Data Services API.</span></span> <span data-ttu-id="8e2c9-106">원래 개방형 Data Services API 중 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 여전히 지원되는 부분은 확장 저장 프로시저뿐이므로 API의 이름이 확장 저장 프로시저 API로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-106">The only part of the original Open Data Services API still supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are the extended stored procedure functions, so the API has been renamed to the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="8e2c9-107">분산 쿼리 및 CLR 통합과 같은 보다 강력한 최신 기술이 등장하면서 확장 저장 프로시저 API 애플리케이션의 필요성이 크게 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-107">With the emergence of newer and more powerful technologies, such as distributed queries and CLR Integration, the need for Extended Stored Procedure API applications has largely been replaced.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e2c9-108">기존 게이트웨이 애플리케이션이 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함된 opends60.dll을 사용하여 해당 애플리케이션을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-108">If you have existing gateway applications, you cannot use the opends60.dll that ships with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run the applications.</span></span> <span data-ttu-id="8e2c9-109">게이트웨이 애플리케이션은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-109">Gateway applications are no longer supported.</span></span>  
  
## <a name="extended-stored-procedures-vs-clr-integration"></a><span data-ttu-id="8e2c9-110">확장 저장 프로시저 및 CLR 통합</span><span class="sxs-lookup"><span data-stu-id="8e2c9-110">Extended Stored Procedures vs. CLR Integration</span></span>  
 <span data-ttu-id="8e2c9-111">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 XP(확장 저장 프로시저)는 데이터베이스 애플리케이션 개발자가 [!INCLUDE[tsql](../../includes/tsql-md.md)]로 표현하기 어렵거나 작성할 수 없는 서버 쪽 논리를 작성할 수 있었던 유일한 메커니즘을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-111">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], extended stored procedures (XPs) provided the only mechanism that was available for database application developers to write server-side logic that was either hard to express or impossible to write in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8e2c9-112">CLR Integration은 이러한 저장 프로시저를 작성하는 보다 강력한 대체 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-112">CLR Integration provides a more robust alternative to writing such stored procedures.</span></span> <span data-ttu-id="8e2c9-113">또한 CLR 통합을 사용할 경우 저장 프로시저의 형태로 작성되던 논리를 보다 효율적인 테이블 반환 함수로 표현할 수 있습니다. 테이블 반환 함수를 통해 함수에서 생성된 결과를 FROM 절에 포함하여 SELECT 문으로 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2c9-113">Furthermore, with CLR Integration, logic that used to be written in the form of stored procedures is often better expressed as table-valued functions, which allow the results constructed by the function to be queried in SELECT statements by embedding them in the FROM clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e2c9-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e2c9-114">See Also</span></span>  
 <span data-ttu-id="8e2c9-115">[공용 언어 런타임 &#40;CLR&#41; 통합 개요](../clr-integration/common-language-runtime-integration-overview.md) </span><span class="sxs-lookup"><span data-stu-id="8e2c9-115">[Common Language Runtime &#40;CLR&#41; Integration Overview](../clr-integration/common-language-runtime-integration-overview.md) </span></span>  
 [<span data-ttu-id="8e2c9-116">CLR 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="8e2c9-116">CLR Table-Valued Functions</span></span>](../clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
  
  
