---
title: 예약 키워드 다음에 콜론 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fc6882439338509a3c716129d9504f209ab1e555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742812"
---
# <a name="remove-colon-following-reserved-keyword"></a><span data-ttu-id="adf2b-102">예약 키워드 다음에 나오는 콜론을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="adf2b-102">Remove colon following reserved keyword</span></span>
  <span data-ttu-id="adf2b-103">업그레이드 관리자가 예약 키워드 뒤에서 콜론(:)이 포함된 스크립트를 감지했습니다.</span><span class="sxs-lookup"><span data-stu-id="adf2b-103">The Upgrade Advisor detected a script that contains a colon (:) following a reserved keyword.</span></span> <span data-ttu-id="adf2b-104">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 구문이 무시되고 문이 성공적으로 실행되지만</span><span class="sxs-lookup"><span data-stu-id="adf2b-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this syntax is ignored and the statements execute successfully.</span></span> <span data-ttu-id="adf2b-105">이제는 데이터베이스 호환성 모드가 100 이상으로 설정된 경우 이 구문 때문에 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="adf2b-105">Now, this syntax causes the statement to fail when the database compatibility mode is set to 100 or later.</span></span>  
  
 <span data-ttu-id="adf2b-106">사용자 데이터베이스는 호환성 모드를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="adf2b-106">User databases maintain their compatibility mode.</span></span>  
  
## <a name="component"></a><span data-ttu-id="adf2b-107">구성 요소</span><span class="sxs-lookup"><span data-stu-id="adf2b-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="adf2b-108">수정 동작</span><span class="sxs-lookup"><span data-stu-id="adf2b-108">Corrective Action</span></span>  
 <span data-ttu-id="adf2b-109">데이터베이스 호환성 모드를 100 이상으로 설정하기 전에 예약 키워드 뒤에 있는 콜론을 제거하여 스크립트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="adf2b-109">Before you change the database compatibility mode to 100 or later, modify your scripts by removing colons that follow reserved keywords.</span></span> <span data-ttu-id="adf2b-110">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "sp_dbcmptlevel"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="adf2b-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf2b-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adf2b-111">See Also</span></span>  
 <span data-ttu-id="adf2b-112">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="adf2b-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="adf2b-113">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="adf2b-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
