---
title: Reporting Services의 SharePoint 라이브러리 배달 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], report delivery
- delivering reports [Reporting Services]
- subscriptions [Reporting Services], SharePoint library delivery
ms.assetid: cb4e4f71-f2d5-475a-9284-ea324c93c7de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5ff109781233ca0c56db0c03ed37bdd13e6e75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739100"
---
# <a name="sharepoint-library-delivery-in-reporting-services"></a><span data-ttu-id="27579-102">Reporting Services의 SharePoint 라이브러리 배달</span><span class="sxs-lookup"><span data-stu-id="27579-102">SharePoint Library Delivery in Reporting Services</span></span>
  <span data-ttu-id="27579-103">SharePoint 통합용으로 구성된 보고서 서버는 보고서를 SharePoint 라이브러리로 보내는 데 사용할 수 있는 배달 확장 프로그램이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-103">A report server that is configured for SharePoint integration includes a delivery extension that you can use to send a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="27579-104">SharePoint 배달 확장 프로그램을 사용하려면 SharePoint 사이트의 애플리케이션 페이지에서 구독을 만든 다음 배달 유형으로 **SharePoint 문서 라이브러리** 를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-104">To use the SharePoint delivery extension, you must create a subscription from an application page on a SharePoint site, and then select **SharePoint document library** as the delivery type.</span></span> <span data-ttu-id="27579-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 또는 보고서 관리자에서 만든 구독에 대해서는 SharePoint 배달 확장 프로그램을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-105">You cannot use the SharePoint delivery extension for subscriptions that you create in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or Report Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27579-106">배달 확장 프로그램은 보고서 서버가 기본 모드로 실행되고 있는 경우 SharePoint 사이트로의 보고서 배달을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-106">The delivery extension does not support the delivery of reports to a SharePoint site if the report server is running in native mode.</span></span> <span data-ttu-id="27579-107">기본 모드 보고서 서버에 대해 프로그래밍 방식으로 배달 확장 프로그램을 호출하려고 하면 서버에서 `rsDeliveryExtensionNotFound` 오류를 반환하고 보고서 서버 로그 파일에 `rsOperationNotSupportedSharePointMode` 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-107">If you attempt to call the delivery extension programmatically for a native mode report server, the server will return the `rsDeliveryExtensionNotFound` error and log the `rsOperationNotSupportedSharePointMode` error in the report server log files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27579-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="27579-108">Requirements</span></span>  
 <span data-ttu-id="27579-109">렌더링된 보고서를 라이브러리에 배달하기 위한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-109">Requirements for delivering rendered reports to a library include the following:</span></span>  
  
-   <span data-ttu-id="27579-110">보고서 서버는 SharePoint 통합 모드용으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-110">The report server must be configured for SharePoint integration mode.</span></span>  
  
-   <span data-ttu-id="27579-111">보고서 서버에 SharePoint 배달 확장 프로그램이 설치 및 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-111">The report server must have the SharePoint delivery extension installed and configured.</span></span>  
  
-   <span data-ttu-id="27579-112">보고서는 보고서 정의 파일(.rdl)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-112">The report must be a report definition (.rdl) file.</span></span> <span data-ttu-id="27579-113">구독을 통해 모델이나 리소스와 같은 다른 보고서 서버 콘텐츠 형식을 배달할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-113">You cannot deliver other report server content types, such as models or resources, through a subscription.</span></span> <span data-ttu-id="27579-114">또한 모델을 데이터 원본으로 사용하는 임시 보고서는 구독할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-114">You cannot subscribe to ad hoc reports that use models as a data source.</span></span>  
  
-   <span data-ttu-id="27579-115">보고서는 저장된 자격 증명을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-115">The report must use stored credentials.</span></span> <span data-ttu-id="27579-116">이는 배달 유형에 관계없이 보고서에 대한 구독을 만들기 위한 선행 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="27579-116">This is a prerequisite for creating any subscription on a report, regardless of the delivery type.</span></span>  
  
-   <span data-ttu-id="27579-117">대상은 SharePoint 라이브러리여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-117">The destination must be a SharePoint library.</span></span> <span data-ttu-id="27579-118">대상 라이브러리를 선택할 때는 동일한 SharePoint 사이트에 있는 라이브러리를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-118">When choosing a target library, you must choose one that is on the same SharePoint site.</span></span> <span data-ttu-id="27579-119">다른 서버 또는 동일한 사이트 모음 내에 있는 다른 사이트의 라이브러리에는 보고서를 배달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-119">You cannot deliver a report to a library on another server or another site within the same site collection.</span></span>  
  
 <span data-ttu-id="27579-120">속성과 메타데이터는 보고서 배달에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-120">Properties and metadata are not part of report delivery.</span></span> <span data-ttu-id="27579-121">보고서는 처음 배달될 때 해당 보고서가 포함된 폴더나 목록의 보안 설정을 상속받습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-121">When the report is delivered for the first time, it inherits the security settings of the folder or list that contains it.</span></span> <span data-ttu-id="27579-122">이후에 보안 설정을 수정하거나 보안 속성을 설정해도 이러한 설정은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="27579-122">If you subsequently modify security settings or set report properties, those settings are retained.</span></span> <span data-ttu-id="27579-123">구독에서는 단순히 지정된 위치에 저장된 보고서를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="27579-123">The subscription just refreshes the report that is stored at the specified location.</span></span>  
  
## <a name="sharepoint-permissions"></a><span data-ttu-id="27579-124">SharePoint 사용 권한</span><span class="sxs-lookup"><span data-stu-id="27579-124">SharePoint Permissions</span></span>  
 <span data-ttu-id="27579-125">구독을 만들려면 보고서에 대한 항목 보기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-125">To create the subscription, you must have View Items permission on the report.</span></span> <span data-ttu-id="27579-126">보고서를 배달하려면 보고서가 배달되는 라이브러리에 대한 항목 추가 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-126">To deliver the report, you must have Add Items permission on the library to which the report is delivered.</span></span>  
  
## <a name="how-to-create-modify-and-delete-subscriptions"></a><span data-ttu-id="27579-127">구독 생성, 수정 및 삭제 방법</span><span class="sxs-lookup"><span data-stu-id="27579-127">How to Create, Modify and Delete Subscriptions</span></span>  
  
1.  <span data-ttu-id="27579-128">보고서에 액세스할 SharePoint 사이트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-128">Go to the SharePoint site from which you access the report.</span></span>  
  
2.  <span data-ttu-id="27579-129">보고서를 선택하고 보고서 옆의 아래쪽 화살표를 클릭한 다음 **구독 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-129">Select the report, click the down arrow next to the report, and select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="27579-130">**만들기**, **편집**또는 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-130">Click **Create**, **Edit**, or **Delete**.</span></span>  
  
 <span data-ttu-id="27579-131">구독 관리 목록의 상태 메시지에 구독 성공 여부 및 구독이 마지막으로 실행된 날짜/시간을 비롯하여 구독에 대한 현재 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27579-131">A Status message on the Manage Subscriptions list displays current information about the subscription, including whether it succeeded and the date and time the subscription last ran.</span></span>  
  
## <a name="setting-delivery-options"></a><span data-ttu-id="27579-132">배달 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="27579-132">Setting Delivery Options</span></span>  
 <span data-ttu-id="27579-133">SharePoint 라이브러리에 보고서를 배달하는 구독에 대해 다음 배달 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-133">You can set the following delivery options on a subscription that delivers a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="27579-134">출력 형식 렌더링</span><span class="sxs-lookup"><span data-stu-id="27579-134">Render output format</span></span>  
 <span data-ttu-id="27579-135">보고서를 배달할 애플리케이션 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-135">Specify the application format in which you want the report delivered.</span></span> <span data-ttu-id="27579-136">보고서는 배달되기 전에 이 형식으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="27579-136">The report is rendered in this format before delivery.</span></span> <span data-ttu-id="27579-137">선택한 출력 형식에 따라 기본 파일 확장명이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="27579-137">The output format you select will determine the default file extension.</span></span>  
  
 <span data-ttu-id="27579-138">선택할 수 있는 출력 형식은 보고서 서버에 설치된 렌더링 확장 프로그램 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="27579-138">The list of output formats you can select from is the set of rendering extensions that are installed on the report server.</span></span>  
  
 <span data-ttu-id="27579-139">내부에서만 사용되거나 SharePoint 통합 모드로 실행되는 보고서 서버에 대해 지원되지 않는 출력 형식은 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-139">Note that you cannot specify output formats that are for internal use only, or that are not supported for report servers that run in SharePoint integrated mode.</span></span> <span data-ttu-id="27579-140">이러한 형식에는 Null, RGDI 및 HTMLOWC가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-140">These formats include Null, RGDI and HTMLOWC.</span></span>  
  
 <span data-ttu-id="27579-141">파일 이름 및 확장명</span><span class="sxs-lookup"><span data-stu-id="27579-141">File name and extension</span></span>  
 <span data-ttu-id="27579-142">대상 라이브러리에 표시할 보고서의 파일 이름과 확장명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-142">Specify the file name and extension of the report as you want it to appear in the target library.</span></span> <span data-ttu-id="27579-143">파일 확장명을 지정하지 않으면 보고서 서버에서 보고서 출력 형식을 기반으로 확장명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27579-143">If you do not specify a file extension, the report server will create one based on the report output format.</span></span> <span data-ttu-id="27579-144">이 값은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="27579-144">This value is required.</span></span> <span data-ttu-id="27579-145">파일 이름에 다음 문자는 포함하지 마세요. : \ / \* ?</span><span class="sxs-lookup"><span data-stu-id="27579-145">The file name must not include the following characters: : \ / \* ?</span></span> <span data-ttu-id="27579-146">" \< > | # { } %</span><span class="sxs-lookup"><span data-stu-id="27579-146">" \< > | # { } %</span></span>  
  
 <span data-ttu-id="27579-147">title</span><span class="sxs-lookup"><span data-stu-id="27579-147">Title</span></span>  
 <span data-ttu-id="27579-148">대상 라이브러리에 있는 보고서의 선택적 `Title` 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-148">Specifies an optional `Title` property for the report in the target library.</span></span> <span data-ttu-id="27579-149">이는 라이브러리에 저장된 모든 항목의 표준 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="27579-149">This is a standard property for all items stored in a library.</span></span> <span data-ttu-id="27579-150">사용자는 SharePoint 사이트의 라이브러리 내용을 볼 때 이 속성을 표시할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-150">Users can specify whether to show or hide this property when viewing library contents on a SharePoint site.</span></span>  
  
 <span data-ttu-id="27579-151">경로</span><span class="sxs-lookup"><span data-stu-id="27579-151">Path</span></span>  
 <span data-ttu-id="27579-152">SharePoint 웹 애플리케이션 및 사이트를 포함하는 SharePoint 라이브러리에 대한 정규화된 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-152">Specifies a fully qualified URL to the SharePoint library, including the SharePoint Web application and site.</span></span> <span data-ttu-id="27579-153">예를 들어 <http://mySharePointWeb/MySite/MyDocLib> , 여기서 " <http://mySharePointWeb> "는 웹 응용 프로그램을 나타내고 "내 사이트"는 sharepoint 사이트 이며 "MyDocLib"는 보고서가 배달 되는 sharepoint 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="27579-153">For example: <http://mySharePointWeb/MySite/MyDocLib>; where "<http://mySharePointWeb>" indicates the Web application, "MySite" is the SharePoint site, and "MyDocLib" is the SharePoint library where the report will be delivered.</span></span>  
  
 <span data-ttu-id="27579-154">페이지, 사이트 또는 목록은 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-154">You cannot specify a page, site, or list.</span></span> <span data-ttu-id="27579-155">대상 컨테이너는 동일한 사이트나 팜에 있는 라이브러리여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-155">The target container must be a library in the same site or farm.</span></span>  
  
 <span data-ttu-id="27579-156">덮어쓰기 옵션</span><span class="sxs-lookup"><span data-stu-id="27579-156">Overwrite options</span></span>  
 <span data-ttu-id="27579-157">구독을 처리할 때 이름과 확장명이 같은 파일을 최신 버전으로 바꿀지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-157">Specifies whether a file with the same name and extension is replaced by a newer version when the subscription is processed.</span></span> <span data-ttu-id="27579-158">기존 파일을 최신 버전으로 바꾸려면 **덮어쓰기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-158">Choose **Overwrite** if you want to replace an existing file with a newer version.</span></span> <span data-ttu-id="27579-159">구독에서 파일을 바꾸지 않도록 하려면 **없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-159">Choose **None** if you do not want the subscription to replace a file.</span></span> <span data-ttu-id="27579-160">이 경우 대상 이름 및 확장명과 동일한 파일이 있으면 배달 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27579-160">In this case, no delivery will occur if a file exists with the target name and extension.</span></span> <span data-ttu-id="27579-161">파일 이름 끝에 번호를 추가하여 동일한 파일의 연속 버전을 추가하려면 **자동 증가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-161">Choose **Autoincrement** if you want to add successive versions of the same file by appending a number at the end of the file name.</span></span>  
  
 <span data-ttu-id="27579-162">자동 복사</span><span class="sxs-lookup"><span data-stu-id="27579-162">Autocopy</span></span>  
 <span data-ttu-id="27579-163">자동 복사 기능을 사용하여 파일의 최신 버전을 자동으로 여러 위치에 복사하는 경우 **덮어쓰기** 가 설정되어 있으면 파일이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="27579-163">If you are using the Autocopy feature to automatically copy the latest version of a file to multiple locations, the file will be copied if **Overwrite** is enabled.</span></span> <span data-ttu-id="27579-164">**Autoincrement** 또는 **None**을 사용 하는 경우 배달이 실패 하 고 `rsDeliveryError` 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="27579-164">If you used **Autoincrement** or **None**, the delivery will fail and the `rsDeliveryError` error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27579-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27579-165">See Also</span></span>  
 <span data-ttu-id="27579-166">[SharePoint 모드 보고서 서버 구독 만들기 및 관리](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="27579-166">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="27579-167">[구독 및 배달&#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="27579-167">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="27579-168">보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정</span><span class="sxs-lookup"><span data-stu-id="27579-168">Specify Credential and Connection Information for Report Data Sources</span></span>](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
