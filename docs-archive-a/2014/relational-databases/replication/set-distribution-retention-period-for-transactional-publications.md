---
title: 트랜잭션 게시에 대 한 배포 보존 기간 설정 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a68f092c63e75196ab82a81d2a8ca36d13142813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661015"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="64d47-102">트랜잭션 게시에 대한 배포 보존 기간 설정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="64d47-102">Set the Distribution Retention Period for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="64d47-103">**배포 데이터베이스 속성 - \<DistributionDatabase>** 대화 상자에서 최소 배포 보존 기간과 최대 배포 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d47-103">Specify the minimum distribution retention period and maximum distribution retention period on the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="64d47-104">이는 **배포자 속성 - \<Distributor>** 대화 상자의 **일반** 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d47-104">This is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="64d47-105">이 대화 상자에 액세스하는 방법은 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="64d47-105">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-distribution-retention-period"></a><span data-ttu-id="64d47-106">배포 보존 기간을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="64d47-106">To specify the distribution retention period</span></span>  
  
1.  <span data-ttu-id="64d47-107">**배포자 속성 - \<Distributor>** 대화 상자의 **일반** 페이지에서 배포 데이터베이스의 속성 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d47-107">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="64d47-108">최소 배포 보존 기간을 지정하려면 **최소** 상자에 값을 입력하고, 최대 배포 보존 기간을 지정하려면 **최대** 상자에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="64d47-108">To specify the minimum distribution retention period, enter a value in the **At least** box; to specify the maximum distribution retention period, enter a value in the **But not more than** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64d47-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64d47-109">See Also</span></span>  
 <span data-ttu-id="64d47-110">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="64d47-110">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="64d47-111">구독 만료 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="64d47-111">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
