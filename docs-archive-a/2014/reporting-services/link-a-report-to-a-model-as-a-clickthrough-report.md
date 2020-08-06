---
title: 보고서를 클릭 광고 보고서로 모델에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cb84f8036dbe5a1694628144f0b948452261ca75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647498"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a><span data-ttu-id="035a8-102">보고서를 클릭 광고 보고서로 모델에 연결</span><span class="sxs-lookup"><span data-stu-id="035a8-102">Link a Report to a Model as a Clickthrough Report</span></span>
  <span data-ttu-id="035a8-103">기본 클릭 광고 보고서 템플릿을 사용하는 대신 보고서 작성기 보고서를 만들고 보고서 모델의 특정 엔터티에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-103">Instead of using the default clickthrough report templates, you can create a Report Builder report and then link it to a specific entity in the report model.</span></span> <span data-ttu-id="035a8-104">보고서를 보는 사람이 주 보고서에서 대화형 데이터를 클릭하면 이 보고서는 클릭 광고 보고서로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-104">When the person viewing the report clicks the interactive data in the main report, this report is displayed as a clickthrough report.</span></span> <span data-ttu-id="035a8-105">엔터티에 보고서를 연결하려면 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-105">To link a report to an entity, use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="035a8-106">보고서에서 사용되는 기본 엔터티는 보고서가 연결되는 동일한 엔터티여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-106">The primary, or base, entity that is used in the report must to be the same entity to which the report is linked.</span></span>  
  
### <a name="to-start-report-manager-from-a-browser"></a><span data-ttu-id="035a8-107">브라우저에서 보고서 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="035a8-107">To start Report Manager from a browser</span></span>  
  
1.  <span data-ttu-id="035a8-108">[!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 이상을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-108">Open [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 or later.</span></span>  
  
2.  <span data-ttu-id="035a8-109">웹 브라우저의 주소 표시줄에 보고서 관리자 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-109">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="035a8-110">기본적으로 URL은 http:///reports입니다. \<*ComputerName*></span><span class="sxs-lookup"><span data-stu-id="035a8-110">By default, the URL is http://\<*ComputerName*>/reports.</span></span>  
  
### <a name="to-create-a-customized-clickthrough-report"></a><span data-ttu-id="035a8-111">사용자 지정 클릭 광고 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="035a8-111">To create a customized clickthrough report</span></span>  
  
1.  <span data-ttu-id="035a8-112">사용자 지정 클릭 광고 보고서를 추가할 보고서 모델로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-112">Navigate to the report model to which you want to add the customized clickthrough report.</span></span>  
  
2.  <span data-ttu-id="035a8-113">보고서 모델을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-113">Double-click the report model.</span></span>  
  
3.  <span data-ttu-id="035a8-114">**클릭 광고**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-114">Click **Clickthrough**.</span></span>  
  
4.  <span data-ttu-id="035a8-115">사용자 지정 클릭 광고 보고서를 연결할 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-115">Select the entity to which you want to attach the customized clickthrough report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="035a8-116">이 엔터티는 사용자 지정 클릭 광고 보고서의 기준 엔터티와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-116">This entity must be the same as the base entity of the customized clickthrough report.</span></span>  
  
5.  <span data-ttu-id="035a8-117">선택한 엔터티의 단일 인스턴스를 클릭할 때 사용자 지정 보고서를 표시하려면 단일 인스턴스 보고서 **찾아보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-117">To display the customized report when a single instance of the selected entity is clicked, click the Single instance report **Browse** button.</span></span>  
  
     <span data-ttu-id="035a8-118">또는</span><span class="sxs-lookup"><span data-stu-id="035a8-118">-or-</span></span>  
  
     <span data-ttu-id="035a8-119">선택한 엔터티의 여러 인스턴스를 클릭할 때 사용자 지정 보고서를 표시하려면 여러 인스턴스 보고서 **찾아보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-119">To display the customized report when a multiple instance of the selected entity is clicked, click the Multiple instance report **Browse** button.</span></span>  
  
6.  <span data-ttu-id="035a8-120">보고서를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-120">Select the report and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="035a8-121">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="035a8-121">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035a8-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="035a8-122">See Also</span></span>  
 [<span data-ttu-id="035a8-123">클릭 광고 보고서 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="035a8-123">Clickthrough Reports &#40;SSRS&#41;</span></span>](reports/clickthrough-reports-ssrs.md)  
  
  
