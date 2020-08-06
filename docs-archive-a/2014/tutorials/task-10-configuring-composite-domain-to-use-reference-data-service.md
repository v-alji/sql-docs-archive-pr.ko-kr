---
title: '작업 10: 참조 데이터 서비스를 사용 하도록 복합 도메인 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d70966b4cde110540bf5008eda4e3151fe32f28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742707"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a><span data-ttu-id="544f7-102">태스크 10: 참조 데이터 서비스를 사용하도록 복합 도메인 구성</span><span class="sxs-lookup"><span data-stu-id="544f7-102">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>
  <span data-ttu-id="544f7-103">이 작업에서는 **Melissa 데이터 주소 검사** 서비스를 사용 하도록 **Address Validation** 복합 도메인을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-103">In this task, you configure the **Address Validation** composite domain to use the **Melissa Data - Address Check** service.</span></span> <span data-ttu-id="544f7-104">런타임에 정리 작업을 수행하는 동안 DQS는 Address Validation 도메인에 있는 도메인 값을 정리하도록 이 서비스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-104">At runtime, during cleansing activity, DQS passes the values of domains in the Address Validation domain to the service for cleansing.</span></span> <span data-ttu-id="544f7-105">자세한 내용은 [참조 데이터에 도메인/복합 도메인 매핑을](https://msdn.microsoft.com/library/hh213030.aspx) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="544f7-105">See [Map Domain/Composite Domain to Reference Data](https://msdn.microsoft.com/library/hh213030.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="544f7-106">**DQS 클라이언트**의 기본 페이지에서 **최근 기술 자료** 아래에 있는 **Suppliers (도메인 관리)** 를 클릭 하 여 **도메인 관리** 페이지를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-106">In the main page of **DQS Client**, click **Suppliers (Domain Management)** under **Recent Knowledge Bases** to launch the **Domain Management** page.</span></span>  
  
2.  <span data-ttu-id="544f7-107">**도메인 목록**에서 **Address Validation** 복합 도메인을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-107">Select the **Address Validation** composite domain in the **list of domains**.</span></span>  
  
3.  <span data-ttu-id="544f7-108">오른쪽 창에서 **참조 데이터** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-108">In the right pane, switch to the **Reference Data** tab.</span></span>  
  
     <span data-ttu-id="544f7-109">![참조 데이터 탭](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "참조 데이터 탭")</span><span class="sxs-lookup"><span data-stu-id="544f7-109">![Reference Data Tab](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "Reference Data Tab")</span></span>  
  
4.  <span data-ttu-id="544f7-110">도구 모음에서 **찾아보기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-110">Click **Browse** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="544f7-111">**온라인 참조 데이터 공급자 카탈로그** 대화 상자에서 **Melissa (데이터 주소 확인)** 옆의 **확인란** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-111">On the **Online Reference Data Providers Catalog** dialog box, select **check box** next to **Melissa Data - Address Check**.</span></span>  
  
     <span data-ttu-id="544f7-112">![Melissa Data - Address Check 선택](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Melissa Data - Address Check 선택")</span><span class="sxs-lookup"><span data-stu-id="544f7-112">![Select Melissa Data - Address Check](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Select Melissa Data - Address Check")</span></span>  
  
6.  <span data-ttu-id="544f7-113">오른쪽 창의 **스키마** 섹션에서 드롭다운 목록을 사용 하 여 address **Line** 도메인을 **address line (M)** 스키마 항목에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-113">In the right pane, in the **Schema** section, map **Address Line** domain to the **Address Line (M)** schema item by using the drop-down list.</span></span>  
  
     <span data-ttu-id="544f7-114">![도메인에 RDS 스키마 항목 매핑](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "도메인에 RDS 스키마 항목 매핑")</span><span class="sxs-lookup"><span data-stu-id="544f7-114">![Map RDS Schema Item to Domain](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "Map RDS Schema Item to Domain")</span></span>  
  
7.  <span data-ttu-id="544f7-115">도구 모음에서 **스키마 항목 추가 (+)** 단추를 클릭 하 여 목록에 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-115">Click **Add Schema Entry (+)** button on the toolbar to create an entry in the list.</span></span>  
  
     <span data-ttu-id="544f7-116">![스키마 항목 추가 도구 모음 단추](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "스키마 항목 추가 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="544f7-116">![Add Schema Entry Toolbar Button](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Add Schema Entry Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="544f7-117">다음 그림에 표시된 것처럼 드롭 다운 목록을 사용해서 다음 DQS 도메인을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-117">Map the following DQS domains by using the drop-down lists as shown in the following picture.</span></span>  
  
     <span data-ttu-id="544f7-118">![도메인에 RDS 스키마 항목 매핑](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "도메인에 RDS 스키마 항목 매핑")</span><span class="sxs-lookup"><span data-stu-id="544f7-118">![Map RDS Schema Items to Domains](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Map RDS Schema Items to Domains")</span></span>  
  
9. <span data-ttu-id="544f7-119">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="544f7-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="544f7-120">다음 단계</span><span class="sxs-lookup"><span data-stu-id="544f7-120">Next Step</span></span>  
 [<span data-ttu-id="544f7-121">태스크 11: 기술 자료 게시</span><span class="sxs-lookup"><span data-stu-id="544f7-121">Task 11: Publishing the Knowledge Base</span></span>](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
