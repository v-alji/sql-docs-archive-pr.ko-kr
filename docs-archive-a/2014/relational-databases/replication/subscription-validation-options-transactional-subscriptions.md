---
title: 구독 유효성 검사 옵션(트랜잭션 구독) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40a617dd1beff24f8f072f5d139bec7c1ca65f33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741755"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a><span data-ttu-id="41d2e-102">구독 유효성 검사 옵션(트랜잭션 구독)</span><span class="sxs-lookup"><span data-stu-id="41d2e-102">Subscription Validation Options (Transactional Subscriptions)</span></span>
  <span data-ttu-id="41d2e-103">**구독 유효성 검사 옵션** 대화 상자를 사용 하 여 유효성 검사에서 행 개수만 사용할지, 아니면 행 개수와 이진 체크섬을 사용할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only, or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="41d2e-104">옵션</span><span class="sxs-lookup"><span data-stu-id="41d2e-104">Options</span></span>  
 <span data-ttu-id="41d2e-105">**구독자와 게시자에 있는 복제된 데이터의 행 개수가 같은지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="41d2e-105">**Verify that the Subscriber has the same number of rows of replicated data as the Publisher**</span></span>  
 <span data-ttu-id="41d2e-106">수행할 행 개수 유효성 검사의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-106">Select the type of row count validation to perform.</span></span> <span data-ttu-id="41d2e-107">Oracle 게시의 경우 **테이블을 직접 쿼리하여 실제 행 개수 컴퓨팅** 옵션만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-107">For Oracle publications, the only available option is **Compute an actual row count by querying the tables directly**.</span></span>  
  
 <span data-ttu-id="41d2e-108">**체크섬을 비교하여 행 데이터 확인**</span><span class="sxs-lookup"><span data-stu-id="41d2e-108">**Compare checksums to verify row data**</span></span>  
 <span data-ttu-id="41d2e-109">게시자 및 구독자에서 행 개수를 확인하고 이진 체크섬 알고리즘을 사용하여 모든 데이터의 체크섬을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-109">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="41d2e-110">행 개수 확인을 실패하면 체크섬 계산이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-110">If the row count fails, the checksum is not performed.</span></span>  
  
 <span data-ttu-id="41d2e-111">**유효성 검사 완료 시 배포 에이전트 중지**</span><span class="sxs-lookup"><span data-stu-id="41d2e-111">**Stop the Distribution Agent after the validation has completed**</span></span>  
 <span data-ttu-id="41d2e-112">기본적으로 배포 에이전트는 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-112">By default, the Distribution Agent runs continuously.</span></span> <span data-ttu-id="41d2e-113">유효성 검사를 수행한 다음 에이전트를 중지하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-113">Select this option to stop the agent after validation is performed.</span></span> <span data-ttu-id="41d2e-114">이 옵션을 사용하면 데이터를 구독자로 복제하기 전에 유효성 검사의 성공 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41d2e-114">This allows you to check whether validation was successful before continuing to replicate data to the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d2e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41d2e-115">See Also</span></span>  
 <span data-ttu-id="41d2e-116">[구독자에서 데이터 유효성 검사](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="41d2e-116">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="41d2e-117">복제된 데이터의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="41d2e-117">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
