---
title: clr enabled 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646647"
---
# <a name="clr-enabled-server-configuration-option"></a><span data-ttu-id="84434-102">clr enabled 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="84434-102">clr enabled Server Configuration Option</span></span>
  <span data-ttu-id="84434-103">clr enabled 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용자 어셈블리를 실행할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84434-103">Use the clr enabled option to specify whether user assemblies can be run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="84434-104">clr enabled 옵션은 다음 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="84434-104">The clr enabled option provides the following values.</span></span>  
  
|<span data-ttu-id="84434-105">값</span><span class="sxs-lookup"><span data-stu-id="84434-105">Value</span></span>|<span data-ttu-id="84434-106">설명</span><span class="sxs-lookup"><span data-stu-id="84434-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84434-107">0</span><span class="sxs-lookup"><span data-stu-id="84434-107">0</span></span>|<span data-ttu-id="84434-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 어셈블리를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84434-108">Assembly execution not allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="84434-109">1</span><span class="sxs-lookup"><span data-stu-id="84434-109">1</span></span>|<span data-ttu-id="84434-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 어셈블리를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84434-110">Assembly execution allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
 <span data-ttu-id="84434-111">이 설정의 변경 내용을 적용하려면 WOW64 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84434-111">WOW64 servers must be restarted before the changes to this setting will take effect.</span></span> <span data-ttu-id="84434-112">다른 서버 유형의 경우에는 서버를 다시 시작하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84434-112">Restart is not required for other server types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84434-113">RECONFIGURE를 실행하고 clr enabled 옵션을 1에서 0으로 변경하면 사용자 어셈블리가 포함된 모든 애플리케이션 도메인이 즉시 언로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="84434-113">When RECONFIGURE is run and the run value of the clr enabled option is changed from 1 to 0, all application domains containing user assemblies are immediately unloaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84434-114">경량 풀링에서는 CLR(공용 언어 런타임) 실행이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84434-114">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="84434-115">두 옵션, 즉 "clr enabled" 또는 "lightweight pooling" 중 하나를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="84434-115">Disable one of two options: "clr enabled" or "lightweight pooling.</span></span> <span data-ttu-id="84434-116">CLR에 의존하며 파이버 모드에서 제대로 작동하지 않는 기능에는 `hierarchy` 데이터 형식, 복제, 정책 기반 관리 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84434-116">Features that rely upon CLR and that do not work properly in fiber mode include the `hierarchy` data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84434-117">예제</span><span class="sxs-lookup"><span data-stu-id="84434-117">Example</span></span>  
 <span data-ttu-id="84434-118">다음 예에서는 먼저 clr enabled 옵션의 현재 설정을 표시한 다음 옵션 값을 1로 설정하여 옵션을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="84434-118">The following example first displays the current setting of the clr enabled option and then enables the option by setting the option value to 1.</span></span> <span data-ttu-id="84434-119">옵션을 해제하려면 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="84434-119">To disable the option, set the value to 0.</span></span>  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="84434-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84434-120">See Also</span></span>  
 <span data-ttu-id="84434-121">[경량 풀링 서버 구성 옵션](lightweight-pooling-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="84434-121">[lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md) </span></span>  
 <span data-ttu-id="84434-122">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="84434-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="84434-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84434-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="84434-124">경량 풀링 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="84434-124">lightweight pooling Server Configuration Option</span></span>](lightweight-pooling-server-configuration-option.md)  
  
  
