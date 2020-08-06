---
title: Sp_helptrigger 출력의 새 열은 응용 프로그램에 영향을 줄 수 있습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660280"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a><span data-ttu-id="8f66c-102">sp_helptrigger의 출력에 나타나는 새 열은 애플리케이션에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f66c-102">New column in output of sp_helptrigger may impact applications</span></span>
  <span data-ttu-id="8f66c-103">sp_helptrigger 시스템 저장 프로시저에서 반환한 결과 집합의 마지막 열을 trigger_schemaias 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f66c-103">trigger_schemaias the last column in the result set returned by the sp_helptrigger system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="8f66c-104">특정 테이블에 정의된 트리거에 대한 정보를 보려면 sys.triggers 카탈로그 뷰를 쿼리하십시오.</span><span class="sxs-lookup"><span data-stu-id="8f66c-104">To obtain information about triggers defined on a particular table, query the sys.triggers catalog view.</span></span>  
  
## <a name="component"></a><span data-ttu-id="8f66c-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8f66c-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="8f66c-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="8f66c-106">Corrective Action</span></span>  
 <span data-ttu-id="8f66c-107">애플리케이션에서 sp_helptrigger의 사용을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="8f66c-107">Review the use of sp_helptrigger in applications.</span></span> <span data-ttu-id="8f66c-108">추가 열을 포함하려면 애플리케이션을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f66c-108">You may need to modify your applications to accommodate the additional column.</span></span> <span data-ttu-id="8f66c-109">또는 sys.triggers 카탈로그 뷰를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f66c-109">Alternatively, you can use the sys.triggers catalog view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f66c-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f66c-110">See Also</span></span>  
 <span data-ttu-id="8f66c-111">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="8f66c-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="8f66c-112">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="8f66c-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
