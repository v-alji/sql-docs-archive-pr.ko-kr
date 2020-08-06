---
title: 기록 보존 기간 설정(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13dcf2ad9a9d619a7fdef9c1ed3f7b970e420cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661014"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a><span data-ttu-id="0a0d2-102">기록 보존 기간 설정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0a0d2-102">Set the History Retention Period (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0a0d2-103">**배포 데이터베이스 속성 - \<DistributionDatabase>** 대화 상자의 **일반** 페이지에서 기록 보존 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-103">Specify the history retention period on the **General** page of the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="0a0d2-104">이 설정은 복제 에이전트 기록이 저장되는 기간을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-104">This setting controls how long replication agent history is stored.</span></span> <span data-ttu-id="0a0d2-105">이 페이지는 **배포자 속성 - \<Distributor>** 대화 상자의 **일반** 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-105">This page is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="0a0d2-106">이 대화 상자에 액세스하는 방법은 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-106">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-history-retention-period"></a><span data-ttu-id="0a0d2-107">기록 보존 기간을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="0a0d2-107">To specify the history retention period</span></span>  
  
1.  <span data-ttu-id="0a0d2-108">**배포자 속성 - \<Distributor>** 대화 상자의 **일반** 페이지에서 배포 데이터베이스의 속성 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-108">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="0a0d2-109">**최소 다음 기간 동안 복제 성능 기록 저장** 상자에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-109">Enter a value in the **Store replication performance history at least** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a0d2-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a0d2-110">See Also</span></span>  
 [<span data-ttu-id="0a0d2-111">배포 구성</span><span class="sxs-lookup"><span data-stu-id="0a0d2-111">Configure Distribution</span></span>](configure-distribution.md)  
  
  
