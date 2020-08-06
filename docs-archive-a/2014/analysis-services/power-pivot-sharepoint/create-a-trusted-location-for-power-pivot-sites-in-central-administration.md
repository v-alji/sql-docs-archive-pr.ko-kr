---
title: 중앙 관리에서 PowerPivot 사이트에 대 한 신뢰할 수 있는 위치 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70b1317db7ce413f3a593056f3b8a140b3bdc446
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653569"
---
# <a name="create-a-trusted-location-for-powerpivot-sites-in-central-administration"></a><span data-ttu-id="cb8b2-102">Create a trusted location for PowerPivot sites in Central Administration</span><span class="sxs-lookup"><span data-stu-id="cb8b2-102">Create a trusted location for PowerPivot sites in Central Administration</span></span>
  <span data-ttu-id="cb8b2-103">Excel 서비스에서는 SharePoint 서버에서 연 통합 문서에 올바른 리포지토리인 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-103">Excel Services lets you specify which locations are valid repositories for workbooks that you open on a SharePoint server.</span></span> <span data-ttu-id="cb8b2-104">이러한 위치를 '신뢰할 수 있는 위치'라고 하며 사용자가 만든 신뢰할 수 있는 위치 각각에 대해 다른 구성 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-104">These locations are called 'trusted locations', and you can use different configuration settings for each trusted location you create.</span></span> <span data-ttu-id="cb8b2-105">SharePoint용 PowerPivot을 배포하는 경우 팜의 나머지 부분에는 기본 설정을 계속 사용하면서 PowerPivot 데이터 액세스에 가장 적합한 설정을 적용할 수 있도록 PowerPivot 통합 문서를 포함하는 사이트에 대한 신뢰할 수 있는 위치를 만드는 것을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-105">For a deployment of PowerPivot for SharePoint, you might consider creating a trusted location for sites that contain PowerPivot workbooks so that you can apply the settings that work best for PowerPivot data access, while preserving default settings for the rest of the farm.</span></span>  
  
  
  
## <a name="prerequisites"></a><span data-ttu-id="cb8b2-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cb8b2-106">Prerequisites</span></span>  
 <span data-ttu-id="cb8b2-107">URL을 신뢰할 수 있는 위치로 지정하려면 팜이나 서비스 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-107">You must be a farm or service administrator to designate a URL as a trusted location.</span></span>  
  
 <span data-ttu-id="cb8b2-108">PowerPivot 갤러리나 통합 문서를 저장하는 기타 라이브러리를 포함하는 SharePoint 사이트의 URL 주소를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-108">You must know the URL address of the SharePoint site that contains the PowerPivot Gallery or other library that stores your workbooks.</span></span> <span data-ttu-id="cb8b2-109">주소를 가져오려면 라이브러리가 포함 된 사이트를 열고 **PowerPivot 갤러리**를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택한 다음 서버 이름과 사이트 경로가 포함 된 주소 (URL)의 첫 부분을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-109">To get the address, open the site that contains the library, right-click **PowerPivot Gallery**, select **Properties**, and then copy the first part of the Address (URL) that contains the server name and site path.</span></span>  
  
##  <a name="overview"></a><a name="overview"></a> <span data-ttu-id="cb8b2-110">개요</span><span class="sxs-lookup"><span data-stu-id="cb8b2-110">Overview</span></span>  
 <span data-ttu-id="cb8b2-111">Excel 서비스의 초기 설치에서는 'http://'를 해당하는 신뢰할 수 있는 위치로 지정합니다. 이는 팜에 있는 모든 사이트의 통합 문서가 서버에서 열릴 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-111">An initial installation of Excel Services specifies 'http://' as its trusted location, which means that workbooks from any site in the farm can be opened on the server.</span></span> <span data-ttu-id="cb8b2-112">신뢰할 수 있는 위치를 더 엄격하게 제어해야 하는 경우 팜에서 특정 사이트에 매핑되는 신뢰할 수 있는 위치를 새로 만든 다음 각 위치에 대해 설정 및 권한을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-112">If you require tighter control over which locations are considered trustworthy, you can create new trusted locations that map to specific sites in your farm, and then vary the settings and permissions for each one.</span></span>  
  
 <span data-ttu-id="cb8b2-113">PowerPivot 통합 문서를 호스팅하는 사이트에 대해 신뢰할 수 있는 위치를 새로 만들면 팜의 나머지 부분에는 기본값을 계속 사용하면서 PowerPivot 데이터 액세스에 가장 적합한 서로 다른 설정을 적용하려는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-113">Creating a new trusted location for sites that host PowerPivot workbooks is especially useful if you want to preserve default values for the rest of the farm, while applying different settings that work best for PowerPivot data access.</span></span> <span data-ttu-id="cb8b2-114">예를 들어 PowerPivot 통합 문서에 대해 최적화된 신뢰할 수 있는 위치에는 50MB의 최대 통합 문서 크기를 사용하고, 팜의 나머지 부분에는 10MB의 기본값을 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-114">For example, a trusted location that is optimized for PowerPivot workbooks could have a maximum workbook size of 50 MB, while the rest of the farm uses the default value of 10MB.</span></span>  
  
 <span data-ttu-id="cb8b2-115">PowerPivot 갤러리 라이브러리를 사용하여 게시된 통합 문서를 미리 볼 때 원하는 미리 보기 이미지가 표시되지 않고 데이터 새로 고침 경고가 표시되는 경우에는 신뢰할 수 있는 위치를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-115">Creating a trusted location is recommended if you are using PowerPivot Gallery libraries to preview published workbooks and you encounter data refresh warnings instead of the preview image you expect.</span></span> <span data-ttu-id="cb8b2-116">PowerPivot 갤러리는 문서 내의 데이터와 표시 정보를 사용하여 보고서와 통합 문서의 축소판 이미지를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-116">PowerPivot Gallery renders thumbnail images of reports and workbooks using data and presentation information within the document.</span></span> <span data-ttu-id="cb8b2-117">신뢰할 수 있는 위치에 대해 새로 고칠 때 경고가 설정되어 있는 경우 PowerPivot 갤러리에 새로 고침을 수행할 권한이 충분하지 않아 축소판 이미지 대신 오류가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-117">If Warn on Data Refresh is enabled for a trusted location, PowerPivot Gallery might not have sufficient permissions to perform the refresh, causing an error to appear instead of the thumbnail image.</span></span> <span data-ttu-id="cb8b2-118">PowerPivot 갤러리를 포함하는 사이트를 새 신뢰할 수 있는 위치로 추가하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-118">Adding a site that contains PowerPivot Gallery as a new trusted location can eliminate this problem.</span></span>  
  
##  <a name="create-a-trusted-location-for-powerpivot-data-access"></a><a name="create"></a><span data-ttu-id="cb8b2-119">PowerPivot 데이터 액세스를 위한 신뢰할 수 있는 위치 만들기</span><span class="sxs-lookup"><span data-stu-id="cb8b2-119">Create a Trusted Location for PowerPivot Data Access</span></span>  
  
1.  <span data-ttu-id="cb8b2-120">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-120">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="cb8b2-121">Excel Services 애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-121">Click the Excel Services Service Application.</span></span>  
  
3.  <span data-ttu-id="cb8b2-122">**신뢰할 수 있는 파일 위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-122">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="cb8b2-123">**신뢰할 수 있는 파일 위치 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-123">Click **Add Trusted File Location**.</span></span>  
  
5.  <span data-ttu-id="cb8b2-124">PowerPivot 갤러리 라이브러리가 포함된 사이트의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-124">Enter the URL of a site that contains a PowerPivot Gallery library.</span></span>  
  
6.  <span data-ttu-id="cb8b2-125">위치 유형에서 **Microsoft SharePoint Foundation**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-125">In Location Type, select **Microsoft SharePoint Foundation**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cb8b2-126">UNC 및 HTTP 위치 유형은 PowerPivot 데이터 액세스에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-126">UNC and HTTP location types are not supported for PowerPivot data access.</span></span>  
  
7.  <span data-ttu-id="cb8b2-127">세션 관리, 통합 문서 속성 및 계산 동작 속성의 모든 기본 설정을 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-127">Accept all of the default settings for properties in Session Management, Workbook Properties, and Calculation Behavior.</span></span>  
  
8.  <span data-ttu-id="cb8b2-128">통합 문서 속성에서 **최대 통합 문서 크기** 를 **50**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-128">In Workbook Properties, set **Maximum Workbook Size** to **50**.</span></span> <span data-ttu-id="cb8b2-129">그러면 통합 문서 파일 크기의 상한이 부모 웹 애플리케이션에 대한 파일 업로드 상한에 맞게 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-129">This aligns the upper limit for workbook file size to the upper limit for file uploads to the parent web application.</span></span> <span data-ttu-id="cb8b2-130">통합 문서가 50MB보다 크면 파일 크기 제한을 더 높여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-130">If your workbooks are larger than 50 megabytes, you must further increase the file size limit.</span></span> <span data-ttu-id="cb8b2-131">자세한 내용은 [SharePoint용 PowerPivot&#41;&#40;최대 파일 업로드 크기 구성 ](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-131">For more information, see [Configure Maximum File Upload Size &#40;PowerPivot for SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).</span></span>  
  
9. <span data-ttu-id="cb8b2-132">외부 데이터에서 외부 데이터 허용이 **신뢰할 수 있는 데이터 연결 라이브러리 및 포함 라이브러리**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-132">In External Data, verify that Allow External Data is set to **Trusted data connection libraries and embedded**.</span></span> <span data-ttu-id="cb8b2-133">통합 문서에서 PowerPivot 데이터에 액세스하려면 이 설정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-133">This setting is required for PowerPivot data access in a workbook.</span></span>  
  
10. <span data-ttu-id="cb8b2-134">외부 데이터에서 새로 고칠 때 경고에 대한 **새로 고침 경고 사용**확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-134">Also in External Data, for Warn on Refresh, clear the checkbox for **Refresh warning enabled**.</span></span> <span data-ttu-id="cb8b2-135">이 확인란 선택을 취소하면 PowerPivot 갤러리가 루틴 경고 메시지를 무시하고 대신 통합 문서의 미리 보기 이미지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-135">Clearing the checkbox allows PowerPivot Gallery to bypass routine warning messages and show preview images of a workbook instead.</span></span>  
  
11. <span data-ttu-id="cb8b2-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb8b2-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8b2-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb8b2-137">See Also</span></span>  
 [<span data-ttu-id="cb8b2-138">PowerPivot 갤러리</span><span class="sxs-lookup"><span data-stu-id="cb8b2-138">PowerPivot Gallery</span></span>](../../index.yml)  
 <span data-ttu-id="cb8b2-139">[PowerPivot 갤러리 만들기 및 사용자 지정](create-and-customize-power-pivot-gallery.md) </span><span class="sxs-lookup"><span data-stu-id="cb8b2-139">[Create and Customize PowerPivot Gallery](create-and-customize-power-pivot-gallery.md) </span></span>  
 [<span data-ttu-id="cb8b2-140">PowerPivot 갤러리 사용</span><span class="sxs-lookup"><span data-stu-id="cb8b2-140">Use PowerPivot Gallery</span></span>](use-power-pivot-gallery.md)  
  
  
