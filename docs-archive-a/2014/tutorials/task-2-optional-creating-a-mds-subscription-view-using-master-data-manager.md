---
title: '작업 2 (선택 사항): 마스터 데이터 관리자를 사용 하 여 MDS 구독 뷰 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 998436734ba5c3cf09cfe88f266a0908c0550abc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735599"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a><span data-ttu-id="2517e-102">태스크 2(선택 사항): 마스터 데이터 관리자를 사용하여 MDS 구독 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="2517e-102">Task 2 (Optional): Creating a MDS Subscription View using Master Data Manager</span></span>
  <span data-ttu-id="2517e-103">이 태스크에서는 **공급자** 모델의 **공급자** 엔터티를 다른 응용 프로그램에 노출 하는 구독 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-103">In this task, you create a subscription view to expose the **Supplier** entity in the **Suppliers** model to other applications.</span></span> <span data-ttu-id="2517e-104">현재 버전의 자습서에서는 이 뷰를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-104">You do not consume this view in the current version of the tutorial.</span></span>  
  
1.  <span data-ttu-id="2517e-105">**Master Data Manager** `http://localhost/MDS` 위쪽에서 **SQL Server 2012 MDS(Master Data Services)** 를 클릭 하 여 마스터 데이터 관리자 ()의 기본 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-105">Switch to the main page of **Master Data Manager** (`http://localhost/MDS`) by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
2.  <span data-ttu-id="2517e-106">**Integration Management**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="2517e-107">메뉴 모음에서 **뷰 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-107">Click **Create Views** on the menu bar.</span></span>  
  
     <span data-ttu-id="2517e-108">![새 구독 뷰 추가 단추](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "새 구독 뷰 추가 단추")</span><span class="sxs-lookup"><span data-stu-id="2517e-108">![Add a New Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Add a New Subscription View Button")</span></span>  
  
4.  <span data-ttu-id="2517e-109">도구 모음에서 **+ (더하기)** 아이콘을 클릭 하 여 구독 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-109">Click **+ (Plus)** icon on the toolbar to create a subscription view.</span></span>  
  
5.  <span data-ttu-id="2517e-110">**구독 뷰 만들기** 창에서 **구독 뷰 이름**으로 **Suppliers** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-110">In the **Create Subscription View** pane, type **Suppliers** for **Subscription view name**.</span></span>  
  
6.  <span data-ttu-id="2517e-111">**모델** 에 대해 **Suppliers**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-111">Select **Suppliers** for **Model**.</span></span>  
  
7.  <span data-ttu-id="2517e-112">**버전** 에 대해 **VERSION_1**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-112">Select **VERSION_1** for **Version**.</span></span>  
  
8.  <span data-ttu-id="2517e-113">**엔터티에**대해 **공급자** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-113">Select **Supplier** for **Entity**.</span></span>  
  
9. <span data-ttu-id="2517e-114">**형식**에 대 한 **리프 멤버** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-114">Select **Leaf members** for **Format**.</span></span>  
  
     <span data-ttu-id="2517e-115">![구독 뷰 저장 단추](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "구독 뷰 저장 단추")</span><span class="sxs-lookup"><span data-stu-id="2517e-115">![Save Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Save Subscription View Button")</span></span>  
  
10. <span data-ttu-id="2517e-116">도구 모음에서 **저장** 을 클릭 하 여 구독 뷰를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-116">Click **Save** on the toolbar to save the subscription view.</span></span> <span data-ttu-id="2517e-117">이 작업을 수행 하면 SQL Server **공급자**라는 보기가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-117">This action creates a view in SQL Server named **Suppliers**.</span></span> <span data-ttu-id="2517e-118">이 뷰는 SSMS(SQL Server Management Studio)를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2517e-118">You can verify this using SQL Server Management Studio (SSMS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2517e-119">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2517e-119">Next Step</span></span>  
 [<span data-ttu-id="2517e-120">작업 3 &#40;옵션&#41;: 구독 뷰 검토</span><span class="sxs-lookup"><span data-stu-id="2517e-120">Task 3 &#40;Optional&#41;: Reviewing the Subscription Views</span></span>](task-3-optional-reviewing-the-subscription-views.md)  
  
  
