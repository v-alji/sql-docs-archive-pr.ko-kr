---
title: 구독 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a61e8b5417bf8312998b5051c47545b705b44c00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638639"
---
# <a name="validate-subscriptions"></a><span data-ttu-id="e98c4-102">구독 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="e98c4-102">Validate Subscriptions</span></span>
  <span data-ttu-id="e98c4-103">**구독 유효성 검사** 대화 상자를 사용하여 각 구독에 대한 배포 에이전트가 다음에 실행될 때 트랜잭션 게시에 대한 구독의 유효성을 검사할지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98c4-103">Use the **Validate Subscriptions** dialog box to specify that subscriptions to a transactional publication should be validated the next time the Distribution Agent for each subscription runs.</span></span> <span data-ttu-id="e98c4-104">유효성 검사 결과는 복제 모니터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98c4-104">The results of validation are displayed in Replication Monitor.</span></span> <span data-ttu-id="e98c4-105">자세한 내용은 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e98c4-105">For more information, see [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e98c4-106">옵션</span><span class="sxs-lookup"><span data-stu-id="e98c4-106">Options</span></span>  
 <span data-ttu-id="e98c4-107">**모든 SQL Server 구독 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="e98c4-107">**Validate all SQL Server subscriptions**</span></span>  
 <span data-ttu-id="e98c4-108">이 게시에 대한 모든 SQL Server 구독 데이터의 유효성을 검사하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e98c4-108">Select to validate data for all SQL Server subscriptions to this publication.</span></span>  
  
 <span data-ttu-id="e98c4-109">**다음 구독 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="e98c4-109">**Validate the following subscriptions**</span></span>  
 <span data-ttu-id="e98c4-110">모든 구독의 유효성을 검사하지 않으려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e98c4-110">Select if you do not want to validate all subscriptions.</span></span> <span data-ttu-id="e98c4-111">목록에서 유효성을 검사할 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e98c4-111">Select from the list the subscriptions you want to validate.</span></span>  
  
 <span data-ttu-id="e98c4-112">**유효성 검사 옵션**</span><span class="sxs-lookup"><span data-stu-id="e98c4-112">**Validation Options**</span></span>  
 <span data-ttu-id="e98c4-113">**구독 유효성 검사 옵션** 대화 상자에 액세스하려면 클릭합니다. 이 대화 상자를 사용하여 행 개수 유효성 검사 또는 이진 체크섬 유효성 검사를 사용할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98c4-113">Click to access the **Subscription Validation Options** dialog box, which allows you to specify whether to use row count validation or binary checksum validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e98c4-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e98c4-114">See Also</span></span>  
 [<span data-ttu-id="e98c4-115">복제된 데이터의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="e98c4-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
