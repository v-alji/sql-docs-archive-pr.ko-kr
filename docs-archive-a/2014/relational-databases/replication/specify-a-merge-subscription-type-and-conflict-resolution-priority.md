---
title: 병합 구독 유형 및 충돌 해결 우선 순위 지정 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743208"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a><span data-ttu-id="8b28b-102">병합 구독 유형 및 충돌 해결 우선 순위 지정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8b28b-102">Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8b28b-103">새 구독 마법사의 **구독 유형** 페이지에서 병합 구독 유형 및 충돌 해결 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b28b-103">Specify a merge subscription type and conflict resolution priority on the **Subscription Type** page of the New Subscription Wizard.</span></span> <span data-ttu-id="8b28b-104">이 마법사의 사용 방법은 [Create a Pull Subscription](create-a-pull-subscription.md) 및 [Create a Push Subscription](create-a-push-subscription.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b28b-104">For more information about using this wizard, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="8b28b-105">구독을 만든 후에는 구독 유형을 수정할 수 없지만 서버 구독 유형의 우선 순위는 **구독 속성 - \<Publisher>: \<PublicationDatabase>** 대화 상자에서 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b28b-105">Subscription type cannot be modified after a subscription is created, but priority can be modified for the server subscription type in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box.</span></span> <span data-ttu-id="8b28b-106">이 대화 상자에 액세스하는 방법은 [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) 및 [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b28b-106">For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a><span data-ttu-id="8b28b-107">병합 구독 유형 및 충돌 해결 우선 순위를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8b28b-107">To specify a merge subscription type and conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="8b28b-108">새 구독 마법사의 **구독 유형** 페이지에서 **구독 유형** 옵션에 대해 **클라이언트** 나 **서버** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8b28b-108">On the **Subscription Type** page of the New Subscription Wizard, select **Client** or **Server** for the **Subscription Type** option.</span></span>  
  
2.  <span data-ttu-id="8b28b-109">구독 유형을 **서버**로 선택한 경우 **충돌 해결의 우선 순위** 에 0.00에서 99.99 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b28b-109">If you select a subscription type of **Server**, also enter a value (0.00 to 99.99) for the **Priority for Conflict Resolution** option.</span></span>  
  
### <a name="to-modify-the-conflict-resolution-priority"></a><span data-ttu-id="8b28b-110">충돌 해결 우선 순위를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8b28b-110">To modify the conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="8b28b-111">게시자의 **구독 속성 - \<Publisher>: \<PublicationDatabase>** 에서 **우선 순위** 옵션에 값(0.00~99.99)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b28b-111">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** at the Publisher, enter a value (0.00 to 99.99) for the **Priority** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b28b-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b28b-112">See Also</span></span>  
 <span data-ttu-id="8b28b-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="8b28b-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="8b28b-114">게시 구독</span><span class="sxs-lookup"><span data-stu-id="8b28b-114">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
