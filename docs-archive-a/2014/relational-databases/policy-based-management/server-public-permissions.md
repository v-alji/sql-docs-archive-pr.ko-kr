---
title: 서버 public 사용 권한 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7913c4715f47b8105b72b1c817dbe77e52d40539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740856"
---
# <a name="server-public-permissions"></a><span data-ttu-id="61dc3-102">서버 public 사용 권한</span><span class="sxs-lookup"><span data-stu-id="61dc3-102">Server public Permissions</span></span>
  <span data-ttu-id="61dc3-103">이 규칙은 public 서버 역할에 서버 사용 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="61dc3-103">This rule determines whether the public server role has server permissions.</span></span> <span data-ttu-id="61dc3-104">서버에 만들어진 모든 로그인은 public 서버 역할의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="61dc3-104">Every login that is created on the server is a member of the public server role.</span></span> <span data-ttu-id="61dc3-105">이 조건이 충족될 경우 서버의 모든 로그인은 서버 사용 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="61dc3-105">If this condition is met, every login on the server will have server permissions.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="61dc3-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="61dc3-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="61dc3-107">서버 public 역할에 서버 사용 권한을 부여하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="61dc3-107">Do not grant server permissions to the server public role.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="61dc3-108">설치가 완료 되 면 **PUBLIC** 역할에는 `CONNECT` **관리자 전용 연결**을 제외한 모든 끝점에 대 한 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61dc3-108">After setup completes the **PUBLIC** role has `CONNECT` permission on all the endpoints except the **Dedicated Admin Connection**.</span></span> <span data-ttu-id="61dc3-109">이것은 정상이며 일반적으로 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="61dc3-109">This is normal and should not be normally changed.</span></span> <span data-ttu-id="61dc3-110">새 로그인을 만들 때 자동으로 부여되는 `CONNECT SQL` 권한으로 액세스가 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="61dc3-110">(Access is controlled by using the `CONNECT SQL` permission which is automatically granted when new logins are created.)</span></span>  
  
### <a name="for-more-information"></a><span data-ttu-id="61dc3-111">참조 항목</span><span class="sxs-lookup"><span data-stu-id="61dc3-111">For more information</span></span>  
 [<span data-ttu-id="61dc3-112">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="61dc3-112">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
  
