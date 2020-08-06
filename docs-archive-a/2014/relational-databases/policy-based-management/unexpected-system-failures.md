---
title: 예기치 않은 시스템 오류 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b791ba0e3f709288a4e2c5b6add4e74e15d56dee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648985"
---
# <a name="unexpected-system-failures"></a><span data-ttu-id="b3018-102">예기치 않은 시스템 오류</span><span class="sxs-lookup"><span data-stu-id="b3018-102">Unexpected System Failures</span></span>
  <span data-ttu-id="b3018-103">이 규칙은 컴퓨터 이벤트 로그에서 SYSTEM 이벤트 6008을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b3018-103">This rule checks for SYSTEM Event 6008 in the computer event log.</span></span> <span data-ttu-id="b3018-104">이 이벤트는 예기치 않은 시스템 종료를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b3018-104">This event indicates an unexpected system shutdown.</span></span> <span data-ttu-id="b3018-105">시스템이 불안정하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 호스팅하는 데 필요한 안정성 및 무결성을 제공하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3018-105">The system might be unstable and might not provide the stability and integrity that is required to host an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="b3018-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="b3018-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="b3018-107">서버가 예기치 않게 다시 시작되는 원인을 찾아 즉시 해결하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다른 컴퓨터로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b3018-107">Immediately address the cause of the unexpected server restarts, or move the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another computer.</span></span>  
  
  
