---
title: OPENXML XPath 식을 업데이트 하 여 지원 되지 않는 함수 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650425"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a><span data-ttu-id="b9a16-102">OPENXML XPath 식을 업데이트하여 지원되지 않는 함수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-102">Update OPENXML XPath expressions to remove unsupported functions</span></span>
  <span data-ttu-id="b9a16-103">업그레이드 관리자가 XPath 기능이 사용되는 것을 감지했습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-103">Upgrade Advisor detected the use of XPath functionality.</span></span> <span data-ttu-id="b9a16-104">업그레이드한 후 OPENXML 기능에 대한 XPath 기능의 변경에 따른 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-104">You may be affected by changes in XPath functionality for OPENXML features after you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b9a16-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b9a16-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b9a16-106">Description</span><span class="sxs-lookup"><span data-stu-id="b9a16-106">Description</span></span>  
 <span data-ttu-id="b9a16-107">이제 MSXML 3.0은 OPENXML 쿼리에 사용된 XPath 식을 처리하는 기본 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-107">MSXML 3.0 is now the underlying engine that is used to process XPath expressions that are used within OPENXML queries.</span></span> <span data-ttu-id="b9a16-108">MSXML 3.0에는 다음 함수를 더 이상 지원하지 않는 좀 더 엄격한 XPath 1.0 엔진이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-108">MSXML 3.0 has a stricter XPath 1.0 engine in which support for the following functions has been removed:</span></span>  
  
-   <span data-ttu-id="b9a16-109">format-number()</span><span class="sxs-lookup"><span data-stu-id="b9a16-109">format-number()</span></span>  
  
-   <span data-ttu-id="b9a16-110">formatNumber()</span><span class="sxs-lookup"><span data-stu-id="b9a16-110">formatNumber()</span></span>  
  
-   <span data-ttu-id="b9a16-111">current()</span><span class="sxs-lookup"><span data-stu-id="b9a16-111">current()</span></span>  
  
-   <span data-ttu-id="b9a16-112">element-available()</span><span class="sxs-lookup"><span data-stu-id="b9a16-112">element-available()</span></span>  
  
-   <span data-ttu-id="b9a16-113">function-available()</span><span class="sxs-lookup"><span data-stu-id="b9a16-113">function-available()</span></span>  
  
-   <span data-ttu-id="b9a16-114">system-property()</span><span class="sxs-lookup"><span data-stu-id="b9a16-114">system-property()</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b9a16-115">수정 동작</span><span class="sxs-lookup"><span data-stu-id="b9a16-115">Corrective Action</span></span>  
 <span data-ttu-id="b9a16-116">format-number() 및 formatNumber()의 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-116">In the case of format-number() and formatNumber(), you can use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b9a16-117">위에 나온 지원되지 않는 다른 함수의 경우에는 직접적인 해결 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a16-117">For the other unsupported functions listed earlier, there is no direct workaround.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a16-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9a16-118">See Also</span></span>  
 <span data-ttu-id="b9a16-119">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b9a16-119">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b9a16-120">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="b9a16-120">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
