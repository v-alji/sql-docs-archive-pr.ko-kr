---
title: allow updates 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7e3ede317509a2044be90635db46e30a932af66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652343"
---
# <a name="allow-updates-server-configuration-option"></a><span data-ttu-id="5bf03-102">allow updates 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="5bf03-102">allow updates Server Configuration Option</span></span>
  <span data-ttu-id="5bf03-103">이 옵션은 **sp_configure** 저장 프로시저에 계속 제공되지만 이 옵션의 기능은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수</span><span class="sxs-lookup"><span data-stu-id="5bf03-103">This option is still present in the **sp_configure** stored procedure, although its functionality is unavailable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5bf03-104">없습니다(설정의 영향 없음).</span><span class="sxs-lookup"><span data-stu-id="5bf03-104">The setting has no effect.</span></span> <span data-ttu-id="5bf03-105">시스템 테이블에 대한 직접 업데이트는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf03-105">Direct updates to the system tables are not supported.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="5bf03-106">**allow updates** 옵션을 변경하면 RECONFIGURE 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf03-106">Changing the **allow updates** option will cause the RECONFIGURE statement to fail.</span></span> <span data-ttu-id="5bf03-107">**allow updates** 옵션에 대한 변경 내용을 모든 스크립트에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf03-107">Changes to the **allow updates** option should be removed from all scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf03-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bf03-108">See Also</span></span>  
 [<span data-ttu-id="5bf03-109">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5bf03-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
