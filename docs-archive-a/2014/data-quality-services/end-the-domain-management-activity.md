---
title: 도메인 관리 작업 종료 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c776674a369bfae8c7da6fa0deabfbd932029570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732044"
---
# <a name="end-the-domain-management-activity"></a><span data-ttu-id="32ee1-102">도메인 관리 작업 종료</span><span class="sxs-lookup"><span data-stu-id="32ee1-102">End the Domain Management Activity</span></span>
  <span data-ttu-id="32ee1-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 도메인 관리 작업 완료, 닫기 또는 취소를 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-103">This topic describes how to complete, close, or cancel the domain management activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="32ee1-104">도메인 관리는 마법사에 의해 수행되지 않으므로 아래 설명된 컨트롤은 도메인 관리 작업의 여러 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-104">Domain management is not performed by a wizard, so the controls described below can used from any of the pages of the domain management activity.</span></span>  
  
## <a name="end-domain-management"></a><span data-ttu-id="32ee1-105">도메인 관리 종료</span><span class="sxs-lookup"><span data-stu-id="32ee1-105">End Domain Management</span></span>  
 <span data-ttu-id="32ee1-106">**마침**</span><span class="sxs-lookup"><span data-stu-id="32ee1-106">**Finish**</span></span>  
 <span data-ttu-id="32ee1-107">도메인 관리를 완료하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-107">Click to complete domain management.</span></span> <span data-ttu-id="32ee1-108">다음 작업을 수행할 수 있는 팝업이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-108">A popup will be displayed enabling you to do the following:</span></span>  
  
-   <span data-ttu-id="32ee1-109">**예 – 기술 자료를 게시하고 끝내기**: 현재 사용자나 다른 사용자가 사용할 수 있도록 기술 자료가 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-109">**Yes - Publish the knowledge base and exit**: The knowledge base will be published for the current user or others to use.</span></span> <span data-ttu-id="32ee1-110">기술 자료가 잠기지 않고 기술 자료 테이블에서 기술 자료의 상태는 비어 있음으로 설정되며 도메인 관리 및 기술 자료 검색 작업을 둘 다 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-110">The knowledge base will not be locked, the state of the knowledge base (in the knowledge base table) will be set to empty, and both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="32ee1-111">기술 자료 열기 화면으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-111">You will be returned to the Open Knowledge Base screen.</span></span>  
  
-   <span data-ttu-id="32ee1-112">**아니요-기술 자료에 대 한 작업을 저장 하 고 종료**: 작업이 저장 되 고 기술 자료가 잠긴 상태로 유지 되며 기술 자료의 상태는 작업 중으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-112">**No - Save the work on the knowledge base and exit**: Your work will be saved, the knowledge base will remained locked, and the state of the knowledge base will be set to In work.</span></span> <span data-ttu-id="32ee1-113">도메인 관리 및 기술 자료 검색 작업을 둘 다 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-113">Both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="32ee1-114">홈 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-114">You will be returned to the home page.</span></span>  
  
-   <span data-ttu-id="32ee1-115">**취소 – 현재 화면에 머무르기**: 팝업이 닫히고 도메인 관리 화면으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-115">**Cancel - Stay on the current screen**: The popup will be closed and you will be returned to the Domain Management screen.</span></span>  
  
 <span data-ttu-id="32ee1-116">**취소**</span><span class="sxs-lookup"><span data-stu-id="32ee1-116">**Cancel**</span></span>  
 <span data-ttu-id="32ee1-117">작업 내용이 손실되어도 도메인 관리 작업을 종료하고 DQS 홈 페이지로 돌아가려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-117">Click to terminate the Domain Management activity, losing your work, and return to the DQS home page.</span></span>  
  
 <span data-ttu-id="32ee1-118">**닫기**</span><span class="sxs-lookup"><span data-stu-id="32ee1-118">**Close**</span></span>  
 <span data-ttu-id="32ee1-119">작업 내용을 저장하고 DQS 홈 페이지로 돌아가려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-119">Click to save your work, and return to the DQS home page.</span></span> <span data-ttu-id="32ee1-120">기술 자료가 잠기며 **기술 자료 열기** 화면의 기술 자료 테이블에서 기술 자료의 상태는 **도메인 관리**가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-120">The knowledge base will be locked, and the state of the knowledge base in the knowledge base table in the **Open Knowledge Base** screen will be **Domain Management**.</span></span> <span data-ttu-id="32ee1-121">**닫기**를 클릭한 후 기술 자료 검색 작업을 수행하려면 **도메인 관리** 화면으로 돌아가서 **마침**을 클릭한 다음 **예** 를 클릭하여 기술 자료를 게시하거나 **아니요** 를 클릭하여 기술 자료에 대한 작업 내용을 저장하고 끝내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32ee1-121">After clicking **Close**, to perform the Knowledge Discovery activity, you would have to return to the **Domain Management** screen, click **Finish**, and then click either **Yes** to publish the knowledge base or **No** to save the work on the knowledge base and exit.</span></span>  <span data-ttu-id="32ee1-122">잠긴 기술 자료를 여는 방법은 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="32ee1-122">For more information on opening a locked knowledge base, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
  
