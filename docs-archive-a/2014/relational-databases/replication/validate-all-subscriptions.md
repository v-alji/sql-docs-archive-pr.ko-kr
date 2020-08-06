---
title: 모든 구독 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27a7a4f5e5c3c303d5a1cbe257c0a0e9b531e824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653261"
---
# <a name="validate-all-subscriptions"></a><span data-ttu-id="90cd5-102">모든 구독 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="90cd5-102">Validate All Subscriptions</span></span>
  <span data-ttu-id="90cd5-103">**모든 구독 유효성 검사** 대화 상자를 사용하여 각 구독에 대한 병합 에이전트가 다음에 실행될 때 병합 게시에 대한 모든 구독의 유효성을 검사할 것인지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-103">Use the **Validate All Subscriptions** dialog box to specify that all subscriptions to a merge publication should be validated the next time the Merge Agent for each subscription runs.</span></span> <span data-ttu-id="90cd5-104">유효성 검사 결과는 복제 모니터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="90cd5-105">자세한 내용은 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90cd5-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="90cd5-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 구독을 마우스 오른쪽 단추로 클릭하고 **구독 유효성 검사**를 클릭하여 단일 구독의 유효성을 검사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-106">It is also possible to validate a single subscription by right-clicking a subscription in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and clicking **Validate Subscription**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="90cd5-107">옵션</span><span class="sxs-lookup"><span data-stu-id="90cd5-107">Options</span></span>  
 <span data-ttu-id="90cd5-108">**행 개수만 확인**</span><span class="sxs-lookup"><span data-stu-id="90cd5-108">**Verify the row counts only**</span></span>  
 <span data-ttu-id="90cd5-109">구독자의 테이블 행 개수가 게시자의 테이블 행 개수와 같은지 확인하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-109">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="90cd5-110">이 방법은 행 내용이 일치하는지 여부는 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-110">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="90cd5-111">행 개수 유효성 검사에서는 최소 수준의 데이터 문제 인식을 위한 검사만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-111">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="90cd5-112">**행 개수를 확인하고 체크섬을 비교하여 행 데이터 확인**</span><span class="sxs-lookup"><span data-stu-id="90cd5-112">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="90cd5-113">게시자 및 구독자에서 행 개수를 확인하고 이진 체크섬 알고리즘을 사용하여 모든 데이터의 체크섬을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-113">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="90cd5-114">행 개수 확인을 실패하면 체크섬 계산이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-114">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="90cd5-115">[!INCLUDE[ssEW](../../includes/ssew-md.md)]에는 이 옵션이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd5-115">This option is not valid for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cd5-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90cd5-116">See Also</span></span>  
 [<span data-ttu-id="90cd5-117">복제된 데이터의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="90cd5-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
