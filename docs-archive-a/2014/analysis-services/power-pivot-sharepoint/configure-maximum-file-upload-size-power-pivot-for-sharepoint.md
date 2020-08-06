---
title: 최대 파일 업로드 크기 구성 (SharePoint용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ac516c63-1e79-4ae8-bca6-32d3c1a09c00
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34a0adb2f22915289cccfa1f21c51038263acca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727379"
---
# <a name="configure-maximum-file-upload-size-powerpivot-for-sharepoint"></a><span data-ttu-id="d54c3-102">최대 파일 업로드 크기 구성(SharePoint용 PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="d54c3-102">Configure Maximum File Upload Size (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="d54c3-103">PowerPivot 통합 문서에 많은 데이터가 포함되어 SharePoint 업로드에 대해 허용되는 최대 파일 크기가 초과되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-103">PowerPivot workbooks often contain large amounts of data that result in files that exceed the maximum file size allowed for SharePoint uploads.</span></span> <span data-ttu-id="d54c3-104">이 상한을 초과하는 파일을 업로드하려고 하면 SharePoint에서</span><span class="sxs-lookup"><span data-stu-id="d54c3-104">When you try to upload a file that exceeds the upper limit, you will get the following error on SharePoint:</span></span>  
  
-   <span data-ttu-id="d54c3-105">“지정된 파일이 지원되는 최대 파일 크기보다 큽니다."라는 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-105">"The specified file is larger than the maximum supported file size."</span></span>  
  
 <span data-ttu-id="d54c3-106">파일 크기를 늘리려면 먼저 Excel 서비스의 최대 통합 문서 크기를 50MB로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-106">To increase the file size, start by adjusting the Maximum Workbook Size for Excel Services to 50 megabytes.</span></span> <span data-ttu-id="d54c3-107">그러면 Excel의 최대 파일 크기 제한이 SharePoint 웹 애플리케이션의 제한에 맞게 조정됩니다(SharePoint 2010에서는 기본적으로 50MB, SharePoint 2013에서는 200MB로 설정됨).</span><span class="sxs-lookup"><span data-stu-id="d54c3-107">This aligns the maximum file size limits for Excel to those of SharePoint web applications (set to 50 megabytes by default in SharePoint 2010 and 200 in SharePoint 2013).</span></span> <span data-ttu-id="d54c3-108">파일 크기가 50MB를 초과하는 경우 Excel 서비스와 웹 애플리케이션의 파일 크기 제한을 모두 높이십시오.</span><span class="sxs-lookup"><span data-stu-id="d54c3-108">If your files exceed 50 megabytes in size, increase the file size limits for both Excel Services and your web application.</span></span>  
  
 <span data-ttu-id="d54c3-109">최대 파일 업로드 크기를 변경하려면 SharePoint 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-109">You must be a SharePoint administrator to change the maximum file upload size.</span></span>  
  
### <a name="configure-maximum-file-size-for-excel-services"></a><span data-ttu-id="d54c3-110">Excel 서비스의 최대 파일 크기 구성</span><span class="sxs-lookup"><span data-stu-id="d54c3-110">Configure maximum file size for Excel Services</span></span>  
  
1.  <span data-ttu-id="d54c3-111">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-111">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="d54c3-112">Excel 서비스 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-112">Click the name of your Excel Services Application.</span></span>  
  
3.  <span data-ttu-id="d54c3-113">**신뢰할 수 있는 파일 위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-113">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="d54c3-114">속성을 편집할 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-114">Click the location to edit the properties.</span></span> <span data-ttu-id="d54c3-115">기본적으로 Excel 서비스는 기본 웹 애플리케이션을 신뢰할 수 있는 사이트로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-115">By default, Excel Services considers the default web application a trusted site.</span></span> <span data-ttu-id="d54c3-116">기본 웹 애플리케이션을 사용 중인 경우 **http://** 를 클릭하여 해당 위치의 구성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-116">If you are using the default web application, click **http://** to open the configuration page for this location.</span></span>  
  
5.  <span data-ttu-id="d54c3-117">**통합 문서 속성**으로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-117">Scroll to **Workbook Properties**.</span></span>  
  
6.  <span data-ttu-id="d54c3-118">최대 통합 문서 크기에서 파일 크기를 10(기본값)에서 50 또는 작업 중인 파일에 맞는 더 큰 값으로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-118">In Maximum Workbook Size, increase the file size from 10 (the default value) to 50 or a larger size that accommodates the files you are working with.</span></span>  
  
     <span data-ttu-id="d54c3-119">기본적으로 SharePoint 웹 애플리케이션의 최대 파일 업로드 크기는 50MB입니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-119">By default, 50 megabytes is the maximum file upload size for SharePoint web applications.</span></span> <span data-ttu-id="d54c3-120">최대 통합 문서 크기를 50MB보다 더 크게 설정하는 경우에는 다음 절차의 단계에 따라 SharePoint 웹 애플리케이션의 최대 업로드 크기도 같은 값으로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-120">If you set Maximum Workbook Size to a number larger than 50 megabytes, follow the steps in the next procedure to increase the Maximum Upload Size for your SharePoint web application to the same value.</span></span>  
  
     <span data-ttu-id="d54c3-121">지정할 수 있는 최대 값은 2GB(또는 중앙 관리에 지정된 대로 2047MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-121">The maximum value that you can specify is 2 gigabytes (or 2047 megabytes as specified in Central Administration).</span></span>  
  
7.  <span data-ttu-id="d54c3-122">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-122">Click **OK**.</span></span>  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a><span data-ttu-id="d54c3-123">SharePoint 웹 애플리케이션의 최대 파일 크기 구성</span><span class="sxs-lookup"><span data-stu-id="d54c3-123">Configure maximum file size for a SharePoint web application</span></span>  
  
1.  <span data-ttu-id="d54c3-124">중앙 관리의 응용 프로그램 관리에서 **웹 응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-124">In Central Administration, in Application Management, click **Manage web applications**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d54c3-125">Excel 서비스의 최대 통합 문서 크기를 증가시킨 경우에만 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-125">Perform the following steps only if you increased the Maximum Workbook Size in Excel Services.</span></span>  
  
2.  <span data-ttu-id="d54c3-126">애플리케이션(예: **SharePoint -80**)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-126">Select the application (for example, **SharePoint - 80**).</span></span>  
  
3.  <span data-ttu-id="d54c3-127">웹 애플리케이션 리본의 일반 설정 단추에서 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-127">On the Web Applications ribbon, click the down arrow on the General Settings button.</span></span>  
  
4.  <span data-ttu-id="d54c3-128">**일반 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-128">Click **General Settings**.</span></span>  
  
5.  <span data-ttu-id="d54c3-129">**최대 업로드 크기**로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-129">Scroll to **Maximum Upload Size**.</span></span>  
  
6.  <span data-ttu-id="d54c3-130">속성을 Excel 서비스의 최대 통합 문서 크기와 같은 값 또는 더 큰 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-130">Set the property to the same number, or larger as the Maximum Workbook Size in Excel Services.</span></span>  
  
7.  <span data-ttu-id="d54c3-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d54c3-131">Click **OK**.</span></span>  
  
  
