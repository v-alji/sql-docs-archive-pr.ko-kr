---
title: 구독 유효성 검사 옵션(병합 구독) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 458da0387dbaa1b366348c374748c42946893feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741759"
---
# <a name="subscription-validation-options-merge-subscriptions"></a><span data-ttu-id="c898d-102">구독 유효성 검사 옵션(병합 구독)</span><span class="sxs-lookup"><span data-stu-id="c898d-102">Subscription Validation Options (Merge Subscriptions)</span></span>
  <span data-ttu-id="c898d-103">**구독 유효성 검사 옵션** 대화 상자를 사용하여 유효성 검사에서 행 개수만 사용할지, 아니면 행 개수와 이진 체크섬을 사용할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c898d-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c898d-104">옵션</span><span class="sxs-lookup"><span data-stu-id="c898d-104">Options</span></span>  
 <span data-ttu-id="c898d-105">**행 개수만 확인**</span><span class="sxs-lookup"><span data-stu-id="c898d-105">**Verify the row counts only**</span></span>  
 <span data-ttu-id="c898d-106">구독자의 테이블 행 개수가 게시자의 테이블 행 개수와 같은지 확인하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c898d-106">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="c898d-107">이 방법은 행 내용이 일치하는지 여부는 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c898d-107">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="c898d-108">행 개수 유효성 검사에서는 최소 수준의 데이터 문제 인식을 위한 검사만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c898d-108">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="c898d-109">**행 개수를 확인하고 체크섬을 비교하여 행 데이터 확인**</span><span class="sxs-lookup"><span data-stu-id="c898d-109">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="c898d-110">게시자 및 구독자에서 행 개수를 확인하고 이진 체크섬 알고리즘을 사용하여 모든 데이터의 체크섬을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="c898d-110">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="c898d-111">행 개수 확인을 실패하면 체크섬 계산이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c898d-111">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="c898d-112">에는이 옵션이 유효 하지 않습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c898d-112">This option is not valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c898d-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c898d-113">See Also</span></span>  
 <span data-ttu-id="c898d-114">[구독자에서 데이터 유효성 검사](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="c898d-114">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="c898d-115">복제된 데이터의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="c898d-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
