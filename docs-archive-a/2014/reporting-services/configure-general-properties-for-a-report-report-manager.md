---
title: 보고서의 일반 속성 구성 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f30900158591afcd5997053dbb61cc22b495ed10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739555"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a><span data-ttu-id="71470-102">일반적인 보고서 속성 구성(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="71470-102">Configure General Properties for a Report (Report Manager)</span></span>
  
### <a name="to-configure-general-report-properties"></a><span data-ttu-id="71470-103">일반적인 보고서 속성을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="71470-103">To configure general report properties</span></span>

1.  <span data-ttu-id="71470-104">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-104">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>

2.  <span data-ttu-id="71470-105">보고서 관리자에서 **내용** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-105">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="71470-106">일반 속성을 구성하려는 보고서로 이동한 후 해당 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="71470-106">Navigate to the report that you want to configure general properties for and open it.</span></span>

3.  <span data-ttu-id="71470-107">**속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-107">Click the **Properties** tab.</span></span>

     <span data-ttu-id="71470-108">또는 **내용** 페이지가 자세히 보기로 표시 되는 경우 속성 페이지 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-108">Or, if the **Contents** page is in Details view, click the property page icon:</span></span>

     <span data-ttu-id="71470-109">![속성 페이지 아이콘](media/prop.gif "속성 페이지 아이콘")</span><span class="sxs-lookup"><span data-stu-id="71470-109">![Property page icon](media/prop.gif "Property page icon")</span></span>

4.  <span data-ttu-id="71470-110">**일반** 속성 페이지가 표시 되 고 다음과 같이 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71470-110">The **General** properties page is displayed, and you can configure properties as follows:</span></span>

    -   <span data-ttu-id="71470-111">**속성** 섹션에서 보고서 이름 및 설명을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71470-111">In the **Properties** section, you can modify the report name and description.</span></span>

    -   <span data-ttu-id="71470-112">**목록 뷰에서 숨기기** 확인란을 선택 하 여 페이지가 기본 페이지 레이아웃 (목록 보기)에서 열릴 때 항목을 숨기고 페이지 간에 항목을 정렬 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71470-112">You can select the **Hide in list view** checkbox to hide the item when the page is opened in the default page layout (list view) which arranges items across and down the page.</span></span>

    -   <span data-ttu-id="71470-113">**보고서 정의** 섹션에서 **편집** 을 클릭 하 여 보고서 정의의 복사본을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-113">In the **Report Definition** section, click **Edit** to extract a copy of the report definition.</span></span> <span data-ttu-id="71470-114">로컬에서 수정한 보고서 정의 내용은 보고서 서버에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71470-114">Modifications that you make locally to the report definition are not saved on the report server.</span></span>

         <span data-ttu-id="71470-115">또는 .rdl 파일에서 보고서 정의를 업데이트 하려면 **업데이트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-115">Or, to update the report definition from an .rdl file, click **Update**.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="71470-116">보고서 정의를 업데이트하는 경우에는 업데이트를 완료한 후 데이터 원본 설정을 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-116">If you update a report definition, you must reset the data source settings after the update is completed.</span></span>

    -   <span data-ttu-id="71470-117">**삭제** 또는 **이동** 단추를 사용 하 여 보고서를 삭제 하거나 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-117">Use the **Delete** or **Move** buttons to delete or move the report.</span></span>

    -   <span data-ttu-id="71470-118">또한 링크된 보고서를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71470-118">You can also create a linked report.</span></span>

5.  <span data-ttu-id="71470-119">보고서의 일반 속성을 구성 하는 작업이 완료 되 면 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="71470-119">When you have finished configuring general properties for the report, click **Apply**.</span></span>

## <a name="see-also"></a><span data-ttu-id="71470-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71470-120">See Also</span></span>
 <span data-ttu-id="71470-121">보고서 관리자&#41;[내용 &#40;페이지](../../2014/reporting-services/contents-page-report-manager.md) [&#40;항목 이동 또는 삭제](report-server/move-or-delete-an-item-report-manager.md) 보고서 관리자&#41;[및 SSRS &#40;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [일반 속성 페이지, 보고서 보고서 작성기 &#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) &#40;</span><span class="sxs-lookup"><span data-stu-id="71470-121">[Move or Delete an Item &#40;Report Manager&#41;](report-server/move-or-delete-an-item-report-manager.md) [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)</span></span>


