---
title: 보고서 파트 찾아보기 및 기본 폴더 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6605a23732799ec07b3dbe8481e88c91b18ebe5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647446"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a><span data-ttu-id="f3e41-102">보고서 파트 찾아보기 및 기본 폴더 설정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f3e41-102">Browse for Report Parts and Set a Default Folder (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f3e41-103">보고서를 만드는 가장 쉬운 방법은 테이블, 차트 등의 기존 보고서 파트를 보고서 파트 갤러리에서 보고서에 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-103">The easiest way to create a report is to add existing report parts, such as tables and charts, to your report from the Report Part Gallery.</span></span> <span data-ttu-id="f3e41-104">보고서 파트를 보고서에 추가할 때는 해당 파트가 작동하는 데 필요한 모든 항목도 추가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-104">When you add a report part to your report, you are also adding everything it must have to work.</span></span> <span data-ttu-id="f3e41-105">예를 들어 데이터를 표시하는 모든 보고서 파트는 데이터 세트, 즉 쿼리와 데이터 원본에 대한 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-105">For example, any report part that displays data depends on a dataset, that is, a query and a connection to a data source.</span></span> <span data-ttu-id="f3e41-106">보고서 파트를 보고서에 추가한 후 필요한 만큼 구성 요소를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-106">After you add the report part to your report, you can modify it as much as you need.</span></span>  
  
 <span data-ttu-id="f3e41-107">보고서 서버 또는 보고서 서버와 통합된 SharePoint 사이트로 보고서 파트를 게시하기 위한 기본 폴더를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-107">You can set a default folder to publish report parts to the report server or SharePoint site integrated with a report server.</span></span>  
  
 <span data-ttu-id="f3e41-108">자세한 내용은 [보고서 파트&#40;보고서 작성기 및 SSRS&#41;](../report-parts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3e41-108">For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-browse-for-report-parts"></a><span data-ttu-id="f3e41-109">보고서 파트를 찾아보려면</span><span class="sxs-lookup"><span data-stu-id="f3e41-109">To browse for report parts</span></span>  
  
1.  <span data-ttu-id="f3e41-110">**삽입** 메뉴에서 **보고서 파트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-110">On the **Insert** menu, click **Report Parts**.</span></span>  
  
     <span data-ttu-id="f3e41-111">아직 연결되어 있지 않은 경우 **보고서 서버에 연결**을 클릭하고 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-111">If you are not already connected, click **Connect to a report server**, and enter the name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3e41-112">보고서 파트를 찾아보려면 보고서 서버에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-112">You must be connected to a report server to browse for report parts.</span></span>  
  
2.  <span data-ttu-id="f3e41-113">보고서 파트에 대한 정보를 지정하여 검색 범위를 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-113">You can narrow your search by specifying details about the report part.</span></span> <span data-ttu-id="f3e41-114">**검색** 상자에 이름과 설명의 전부 또는 일부를 입력하거나 **조건 추가** 를 클릭하고 다음 필드 중 하나나 모두의 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-114">Type all or part of the name and description in the **Search** box, or click **Add Criteria** and add values for any or all of these fields:</span></span>  
  
    -   <span data-ttu-id="f3e41-115">만든 사람</span><span class="sxs-lookup"><span data-stu-id="f3e41-115">Created by</span></span>  
  
    -   <span data-ttu-id="f3e41-116">만든 날짜</span><span class="sxs-lookup"><span data-stu-id="f3e41-116">Date created</span></span>  
  
    -   <span data-ttu-id="f3e41-117">마지막으로 수정한 날짜</span><span class="sxs-lookup"><span data-stu-id="f3e41-117">Date last modified</span></span>  
  
    -   <span data-ttu-id="f3e41-118">마지막으로 수정한 사람</span><span class="sxs-lookup"><span data-stu-id="f3e41-118">Last modified by</span></span>  
  
    -   <span data-ttu-id="f3e41-119">서버 폴더</span><span class="sxs-lookup"><span data-stu-id="f3e41-119">Server folder</span></span>  
  
    -   <span data-ttu-id="f3e41-120">Type</span><span class="sxs-lookup"><span data-stu-id="f3e41-120">Type</span></span>  
  
     <span data-ttu-id="f3e41-121">예를 들어 이미지를 찾으려면 **조건 추가**를 클릭하고 **유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-121">For example, to find an image, click **Add Criteria**, and then click **Type**.</span></span> <span data-ttu-id="f3e41-122">드롭다운 상자에서 **이미지** 확인란을 선택하고 ENTER 키를 누르고 검색 돋보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-122">In the dropdown box, select the **Image** check box, press ENTER, and then click the Search magnifying glass.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3e41-123">**만든 사람** 및 **마지막으로 수정한 사람** 값의 경우에는 보고서 서버에 표시되어 있는 사람의 사용자 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-123">For the **Created by** and **Last modified by** values, search for the person's user name as it is represented on the report server.</span></span>  
  
### <a name="to-set-a-default-folder-for-report-parts"></a><span data-ttu-id="f3e41-124">보고서 파트의 기본 폴더를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f3e41-124">To set a default folder for report parts</span></span>  
  
1.  <span data-ttu-id="f3e41-125">**보고서 작성기**를 클릭한 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-125">Click **Report Builder**, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="f3e41-126">**옵션** 대화 상자의 **설정** 탭에 있는 **다음 폴더에 보고서 파트를 기본적으로 게시** 입력란에 폴더 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-126">In the **Options** dialog box, on the **Settings** tab, type a folder name in the **Publish report parts to this folder by default** textbox.</span></span>  
  
 <span data-ttu-id="f3e41-127">보고서 서버에 폴더를 만들 수 있는 권한이 있는 경우 이 폴더가 없으면 보고서 작성기가 이 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-127">Report Builder will create this folder if you have permissions to create folders on the report server and the folder does not exist yet.</span></span>  
  
 <span data-ttu-id="f3e41-128">이 설정을 적용하기 위해 보고서 작성기를 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3e41-128">You do not need to restart Report Builder for this setting to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e41-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3e41-129">See Also</span></span>  
 <span data-ttu-id="f3e41-130">[업데이트를 확인 하거나 업데이트 &#40;보고서 작성기 및 SSRS를 해제&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f3e41-130">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f3e41-131">[보고서 파트&#40;보고서 작성기 및 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f3e41-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f3e41-132">[보고서 작성기의 보고서 파트 및 데이터 세트](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="f3e41-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="f3e41-133">[보고서 파트 &#40;보고서 작성기 및 SSRS에 대 한 문제 해결&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f3e41-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f3e41-134">보고서 파트 게시 및 다시 게시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f3e41-134">Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;</span></span>](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
