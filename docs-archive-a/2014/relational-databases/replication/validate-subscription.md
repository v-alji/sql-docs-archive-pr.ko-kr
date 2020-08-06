---
title: 구독 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 010b5b2e9778ccf37133b0a84796373c012290f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648915"
---
# <a name="validate-subscription"></a><span data-ttu-id="f3578-102">구독 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="f3578-102">Validate Subscription</span></span>
  <span data-ttu-id="f3578-103">**구독 유효성 검사** 대화 상자를 사용하여 다음에 구독에 대한 병합 에이전트가 실행될 때 병합 게시에 대한 해당 구독의 유효성을 검사하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-103">Use the **Validate Subscription** dialog box to specify that a subscription to a merge publication should be validated the next time the Merge Agent for the subscription runs.</span></span> <span data-ttu-id="f3578-104">유효성 검사 결과는 복제 모니터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="f3578-105">자세한 내용은 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3578-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="f3578-106">또한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시를 마우스 오른쪽 단추로 클릭하고 **모든 구독 유효성 검사**를 클릭하여 병합 게시에 대한 모든 구독의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-106">It is also possible to validate all subscriptions to a merge publication by right-clicking a publication in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate All Subscriptions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3578-107">옵션</span><span class="sxs-lookup"><span data-stu-id="f3578-107">Options</span></span>  
 <span data-ttu-id="f3578-108">**마지막으로 유효성 검사를 시도한 날짜**</span><span class="sxs-lookup"><span data-stu-id="f3578-108">**Date of the last attempted validation**</span></span>  
 <span data-ttu-id="f3578-109">유효성 검사의 성공 여부에 상관없이 구독 유효성 검사가 포함된 마지막 병합 에이전트 세션의 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-109">The date of the last Merge Agent session that included subscription validation, whether or not that validation was successful.</span></span>  
  
 <span data-ttu-id="f3578-110">**마지막으로 유효성 검사를 성공한 날짜**</span><span class="sxs-lookup"><span data-stu-id="f3578-110">**Date of the last successful validation**</span></span>  
 <span data-ttu-id="f3578-111">성공한 구독 유효성 검사가 포함된 마지막 병합 에이전트 세션의 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-111">The date of the last Merge Agent session that included a successful subscription validation.</span></span>  
  
 <span data-ttu-id="f3578-112">**이 구독 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="f3578-112">**Validate this subscription**</span></span>  
 <span data-ttu-id="f3578-113">구독 유효성을 검사하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-113">Select to validate the subscription.</span></span>  
  
 <span data-ttu-id="f3578-114">**옵션**</span><span class="sxs-lookup"><span data-stu-id="f3578-114">**Options**</span></span>  
 <span data-ttu-id="f3578-115">**구독 유효성 검사 옵션** 대화 상자에 액세스하려면 클릭합니다. 이 대화 상자를 사용하여 행 개수 유효성 검사 또는 이진 체크섬 유효성 검사를 사용할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3578-115">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3578-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3578-116">See Also</span></span>  
 [<span data-ttu-id="f3578-117">복제된 데이터의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="f3578-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
