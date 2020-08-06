---
title: 보고서 파트 게시 및 다시 게시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92dce484-f39b-403c-9caf-d8772bc3aca3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95fd5e3f7519c6a0d4a6f08cb9bcbf2507d32aaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649379"
---
# <a name="publish-and-republish-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="9fd65-102">보고서 파트 게시 및 다시 게시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9fd65-102">Publish and Republish Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9fd65-103">보고서 파트는 기본 설정으로 기본 위치에 게시할 수도 있고 이름, 설명 등의 보고서 파트 메타데이터를 편집한 다음 보고서 서버의 다른 위치에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-103">You can publish a report part with default settings in a default location, or you can edit report part metadata such as name and description, and save it somewhere else on a report server.</span></span> <span data-ttu-id="9fd65-104">또한 올바른 권한이 있는 경우에는 보고서 서버와 통합된 SharePoint 사이트에 보고서 파트를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-104">You can also save it to a SharePoint site that is integrated with a report server if you have the correct permissions.</span></span>  
  
 <span data-ttu-id="9fd65-105">보고서 파트가 사용하는 데이터 세트를 포함하여 보고서 파트만 게시하거나 데이터 세트를 별도로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-105">You can publish just the report part, with the dataset that it depends on embedded in it, or you can publish the dataset separately.</span></span> <span data-ttu-id="9fd65-106">데이터 세트를 별도로 게시하는 경우에는 공유 데이터 세트가 되며 보고서 파트가 이 데이터 세트에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-106">If you publish the dataset separately, it becomes a shared dataset, and the report part links to it.</span></span> <span data-ttu-id="9fd65-107">자세한 내용은 [보고서 작성기의 보고서 파트 및 데이터 세트](../report-data/report-parts-and-datasets-in-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fd65-107">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="9fd65-108">기존 보고서 파트를 다시 게시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-108">You can republish an existing report part.</span></span> <span data-ttu-id="9fd65-109">권한이 있는 경우에는 서버에 있는 보고서 파트(자신이 만든 것이 아니어도 됨)의 원본 인스턴스를 덮어써 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-109">If you have permissions, you can save over the original instance of the report part on the server, even if you didn't create it.</span></span> <span data-ttu-id="9fd65-110">또한 새 보고서 파트로 게시한 다음 같은 위치나 다른 위치에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-110">You can also publish it as a new report part and save it either in the same or a different location.</span></span>  
  
### <a name="to-publish-a-report-part"></a><span data-ttu-id="9fd65-111">보고서 파트를 게시하려면</span><span class="sxs-lookup"><span data-stu-id="9fd65-111">To publish a report part</span></span>  
  
1.  <span data-ttu-id="9fd65-112">보고서 작성기 메뉴에서 **보고서 파트 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-112">On the Report Builder menu, click **Publish Report Parts**.</span></span>  
  
     <span data-ttu-id="9fd65-113">보고서 서버에 연결되어 있지 않은 경우에는 연결하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-113">If you are not connected to a report server, you will be prompted to connect.</span></span> <span data-ttu-id="9fd65-114">보고서 서버에 연결할 수 없으면 보고서 파트를 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-114">If you cannot connect to a report server, you cannot publish report parts.</span></span>  
  
2.  <span data-ttu-id="9fd65-115">보고서 파트를 기본 설정으로 기본 위치에 저장하려면 **모든 보고서 파트를 기본 설정으로 게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-115">To save your report parts with default settings to the default location, click **Publish all report parts with default settings**.</span></span>  
  
     <span data-ttu-id="9fd65-116">그렇지 않으면 **게시하기 전에 보고서 파트 검토 및 수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-116">Otherwise, click **Review and modify report parts before publishing**.</span></span>  
  
3.  <span data-ttu-id="9fd65-117">보고서 파트 이름 및 설명을 편집하려면 이름을 두 번 클릭해 편집하고 **설명** 필드를 클릭해 설명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-117">Edit the report part name and description: Double-click the name to edit it and click in the **Description** field to add a description.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9fd65-118">다른 사람들이 검색할 때 쉽게 식별할 수 있도록 명확한 보고서 파트 이름과 설명을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-118">It is a good idea to give the report part name and description, to help people identify it when searching.</span></span> <span data-ttu-id="9fd65-119">보고서 파트 이름의 최대 길이는 260자(전체 경로)입니다. 여기에는 서버의 폴더 이름 뒤에 보고서 파트의 실제 이름이 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-119">The maximum length for the name of a report part is 260 characters for the entire path, including the names of the folders on the server, followed by the actual name of the report part.</span></span>  
  
4.  <span data-ttu-id="9fd65-120">보고서 파트를 기본 폴더가 아닌 다른 폴더에 저장하려면 **찾아보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-120">To save your report part to a folder other than the default, click the **Browse** button.</span></span>  
  
5.  <span data-ttu-id="9fd65-121">보고서의 모든 보고서 파트에 대한 옵션을 설정했으면 **게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-121">When you have set the options for all the report parts in the report, click **Publish**.</span></span>  
  
     <span data-ttu-id="9fd65-122">보고서 파트를 게시하고 나면 대화 상자에 제대로 게시된 항목과 그렇지 않은 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-122">After you publish the report parts, the dialog box shows which were successfully published and which were not.</span></span> <span data-ttu-id="9fd65-123">**보고서 파트 게시** 대화 상자에서 게시되지 않은 보고서 파트에 대한 상세 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-123">You can view details in the **Publish Report Parts** dialog box for the report parts that failed to publish.</span></span>  
  
6.  <span data-ttu-id="9fd65-124">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-124">Click **Close**.</span></span>  
  
### <a name="to-republish-a-report-part"></a><span data-ttu-id="9fd65-125">보고서 파트를 다시 게시하려면</span><span class="sxs-lookup"><span data-stu-id="9fd65-125">To republish a report part</span></span>  
  
1.  <span data-ttu-id="9fd65-126">이전 절차에 따라 보고서 파트를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-126">Follow the previous procedure for publishing a report part.</span></span>  
  
2.  <span data-ttu-id="9fd65-127">**보고서 파트 게시** 대화 상자에서 **보고서 항목의 새 복사본으로 게시**를 클릭하면 보고서 작성기에서 서버의 기존 보고서 파트를 덮어써 저장하지 않고 다른 보고서 파트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-127">In the **Publish Report Parts** dialog box, if you click **Publish as a New Copy of the Report Part**, Report Builder will not save over the existing report part on the server, but will create another report part instead.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9fd65-128">새 보고서 파트로 게시하는 경우에는 새 고유 ID가 지정되며</span><span class="sxs-lookup"><span data-stu-id="9fd65-128">If you publish it as a new report part, it will have a new unique ID.</span></span> <span data-ttu-id="9fd65-129">원본 보고서 파트를 변경해도 더 이상 업데이트를 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd65-129">It will no longer receive updates if the original report part changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd65-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fd65-130">See Also</span></span>  
 <span data-ttu-id="9fd65-131">[보고서 파트 &#40;보고서 작성기 및 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9fd65-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9fd65-132">[보고서 작성기의 보고서 파트 및 데이터 집합](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="9fd65-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="9fd65-133">[보고서 파트 &#40;보고서 작성기 및 SSRS에 대 한 문제 해결&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9fd65-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9fd65-134">[업데이트를 확인 하거나 업데이트 &#40;보고서 작성기 및 SSRS를 해제&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9fd65-134">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9fd65-135">보고서 파트 찾아보기 및 기본 폴더 설정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9fd65-135">Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;</span></span>](browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)  
  
  
