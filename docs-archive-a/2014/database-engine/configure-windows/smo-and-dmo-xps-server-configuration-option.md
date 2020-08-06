---
title: SMO and DMO XPs 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f18fc6fafcf033113c983f990700158a10aec92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740408"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a><span data-ttu-id="b9690-102">SMO and DMO XPs 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="b9690-102">SMO and DMO XPs Server Configuration Option</span></span>
  <span data-ttu-id="b9690-103">SMO 및 DMO XP 옵션을 사용하여 현재 서버에서 SMO( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object) 확장 저장 프로시저를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-103">Use the SMO and DMO XPs option to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) extended stored procedures on this server.</span></span>  
  
 <span data-ttu-id="b9690-104">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터 DMO는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-104">Note than beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO has been removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b9690-105">다음 표에서는 이 옵션에 사용할 수 있는 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-105">The possible values are described in the following table:</span></span>  
  
|<span data-ttu-id="b9690-106">값</span><span class="sxs-lookup"><span data-stu-id="b9690-106">Value</span></span>|<span data-ttu-id="b9690-107">의미</span><span class="sxs-lookup"><span data-stu-id="b9690-107">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="b9690-108">0</span><span class="sxs-lookup"><span data-stu-id="b9690-108">0</span></span>|<span data-ttu-id="b9690-109">SMO XP를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-109">SMO XPs are not available.</span></span>|  
|<span data-ttu-id="b9690-110">1</span><span class="sxs-lookup"><span data-stu-id="b9690-110">1</span></span>|<span data-ttu-id="b9690-111">SMO XP를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-111">SMO XPs are available.</span></span> <span data-ttu-id="b9690-112">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-112">This is the default.</span></span>|  
  
 <span data-ttu-id="b9690-113">설정은 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-113">The setting takes effect immediately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b9690-114">예제</span><span class="sxs-lookup"><span data-stu-id="b9690-114">Examples</span></span>  
 <span data-ttu-id="b9690-115">다음 예에서는 SMO 확장 저장 프로시저를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b9690-115">The following example enables SMO extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9690-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9690-116">See Also</span></span>  
 [<span data-ttu-id="b9690-117">SMO&#40;SQL Server 관리 개체&#41; 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="b9690-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
