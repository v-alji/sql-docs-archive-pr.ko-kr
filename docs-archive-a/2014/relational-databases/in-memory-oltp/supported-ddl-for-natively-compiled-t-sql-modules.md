---
title: 고유 하 게 컴파일된 저장 프로시저에서 지원 되는 구문 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
ms.openlocfilehash: f3bc7e28fa2a868ac39c6adbb2dea3cc5c3ace73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649549"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a><span data-ttu-id="7e182-102">고유하게 컴파일된 저장 프로시저의 지원되는 구문</span><span class="sxs-lookup"><span data-stu-id="7e182-102">Supported Constructs on Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="7e182-103">이 항목에서는 고유하게 컴파일된 저장 프로시저에서 지원되는 구문에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7e182-103">This topic lists the supported constructs on natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="7e182-104">지원되지 않는 구문에 대한 정보는 [메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문](transact-sql-constructs-not-supported-by-in-memory-oltp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e182-104">For information about unsupported constructs, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="procedure-ddl"></a><span data-ttu-id="7e182-105">프로시저 DDL</span><span class="sxs-lookup"><span data-stu-id="7e182-105">Procedure DDL</span></span>  
 <span data-ttu-id="7e182-106">다음 항목이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e182-106">The following are supported:</span></span>  
  
-   <span data-ttu-id="7e182-107">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="7e182-107">CREATE PROCEDURE</span></span>  
  
-   <span data-ttu-id="7e182-108">DROP PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="7e182-108">DROP PROCEDURE</span></span>  
  
-   <span data-ttu-id="7e182-109">SCHEMABINDING(고유하게 컴파일된 저장 프로시저에 필요함)</span><span class="sxs-lookup"><span data-stu-id="7e182-109">SCHEMABINDING (required for natively compiled stored procedures)</span></span>  
  
-   <span data-ttu-id="7e182-110">NATIVE_COMPILATION</span><span class="sxs-lookup"><span data-stu-id="7e182-110">NATIVE_COMPILATION</span></span>  
  
-   <span data-ttu-id="7e182-111">매개 변수는 NOT NULL로 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e182-111">Parameters can be declared as NOT NULL.</span></span>  
  
-   <span data-ttu-id="7e182-112">테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="7e182-112">Table-valued parameters.</span></span>  
  
## <a name="security"></a><span data-ttu-id="7e182-113">보안</span><span class="sxs-lookup"><span data-stu-id="7e182-113">Security</span></span>  
 <span data-ttu-id="7e182-114">다음 항목이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e182-114">The following are supported:</span></span>  
  
-   <span data-ttu-id="7e182-115">프로시저: EXECUTE AS OWNER, SELF 및 사용자</span><span class="sxs-lookup"><span data-stu-id="7e182-115">For procedures: EXECUTE AS OWNER, SELF, and user.</span></span>  
  
-   <span data-ttu-id="7e182-116">테이블 및 프로시저에 대한 GRANT 및 DENY 권한</span><span class="sxs-lookup"><span data-stu-id="7e182-116">GRANT and DENY permissions on tables and procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e182-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e182-117">See Also</span></span>  
 [<span data-ttu-id="7e182-118">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="7e182-118">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
