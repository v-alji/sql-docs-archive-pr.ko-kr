---
title: 보고서 또는 모델을 공유 데이터 원본에 바인딩(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 596caba042d476173b3c49d1ad18e79d0827fe89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730200"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a><span data-ttu-id="f07cd-102">보고서 또는 모델을 공유 데이터 원본에 바인딩(SSRS)</span><span class="sxs-lookup"><span data-stu-id="f07cd-102">Bind a Report or Model to a Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="f07cd-103">보고서나 모델을 테스트 서버에서 프로덕션 서버로 이동할 때와 같이 로컬 컴퓨터에 파일을 저장한 다음 이 파일을 다른 보고서 서버로 업로드해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-103">In some situations, such as when you move a report or model from a test server to a production server, you might want to save the file to your local computer and then upload it to a different report server.</span></span> <span data-ttu-id="f07cd-104">보고서나 모델을 새 서버로 업로드하는 경우 새 보고서 서버에 저장된 공유 데이터 원본에 다시 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-104">When you upload the report or model to the new server, you need to rebind it to a shared data source that is stored on the new report server.</span></span> <span data-ttu-id="f07cd-105">보고서나 모델을 다시 바인딩하지 않으면 새 보고서 서버에서 액세스할 때 제대로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-105">If you don't rebind the report or model, it will not work correctly when accessed from the new report server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f07cd-106">보고서나 모델을 공유 데이터 원본에 다시 바인딩하기 전에 보고서 서버나 SharePoint 라이브러리에 이미 데이터 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-106">Before rebinding a report or model to a shared data source, the data source must already exist on the report server or SharePoint library.</span></span> <span data-ttu-id="f07cd-107">데이터 원본에 대한 자세한 내용은 [공유 데이터 원본 만들기, 수정 및 삭제&#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f07cd-107">For more information about data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a><span data-ttu-id="f07cd-108">보고서나 모델을 기본 모드로 실행되는 보고서 서버의 공유 데이터 원본에 바인딩하려면</span><span class="sxs-lookup"><span data-stu-id="f07cd-108">To bind a report or model to a shared data source on a report server running in native mode</span></span>  
  
1.  <span data-ttu-id="f07cd-109">**보고서 관리자**에서 서버로 업로드할 보고서나 모델의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-109">In **Report Manager**, click the name of the report or model that you uploaded to the server.</span></span>  
  
     <span data-ttu-id="f07cd-110">속성 탭이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-110">The Properties tab opens.</span></span>  
  
2.  <span data-ttu-id="f07cd-111">**데이터 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-111">Click **Data Sources**.</span></span>  
  
3.  <span data-ttu-id="f07cd-112">**찾아보기**를 클릭한 다음 보고서나 모델을 바인딩할 데이터 원본을 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-112">Click **Browse**, and then navigate to the data source to which you want to bind the report or model.</span></span>  
  
4.  <span data-ttu-id="f07cd-113">데이터 원본을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-113">Select the data source and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f07cd-114">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-114">Click **Apply**.</span></span>  
  
     <span data-ttu-id="f07cd-115">이제 보고서나 모델이 선택한 데이터 원본에 바인딩되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-115">The report or model is now bound to the data source that you selected.</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a><span data-ttu-id="f07cd-116">보고서나 모델을 SharePoint 통합 모드로 실행되는 보고서 서버의 공유 데이터 원본에 바인딩하려면</span><span class="sxs-lookup"><span data-stu-id="f07cd-116">To bind a report or model to a shared data source on a report server running in SharePoint integrated mode</span></span>  
  
1.  <span data-ttu-id="f07cd-117">라이브러리가 아직 열려 있지 않으면 빠른 실행 표시줄에서 해당 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-117">If the library is not already open, click its name on the Quick Launch bar.</span></span> <span data-ttu-id="f07cd-118">라이브러리 이름이 나타나지 않으면 **모든 사이트 콘텐츠 보기**를 클릭한 다음 라이브러리 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-118">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="f07cd-119">보고서나 모델을 가리키고 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-119">Point to the report or model and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="f07cd-120">**데이터 원본 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-120">Click **Manage Data Sources**.</span></span>  
  
4.  <span data-ttu-id="f07cd-121">**dataSource1**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-121">Click **dataSource1**.</span></span>  
  
5.  <span data-ttu-id="f07cd-122">**연결 형식** 영역에서 **공유 데이터 원본** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-122">In the **Connection Type** area, verify that **Shared data source** is selected.</span></span>  
  
6.  <span data-ttu-id="f07cd-123">**데이터 원본 링크** 영역에서 줄임표 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-123">In the **Data Source Link** area, click the ellipsis (...) button.</span></span>  
  
7.  <span data-ttu-id="f07cd-124">사용할 데이터 원본을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-124">Locate the data source you want to use.</span></span>  
  
8.  <span data-ttu-id="f07cd-125">데이터 원본을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-125">Select the data source and **click OK**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="f07cd-126">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f07cd-126">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07cd-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f07cd-127">See Also</span></span>  
 <span data-ttu-id="f07cd-128">[보고서 관리자&#41;&#40;파일 또는 보고서 업로드](../reports/upload-a-file-or-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f07cd-128">[Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md) </span></span>  
 <span data-ttu-id="f07cd-129">[Sharepoint 라이브러리에 문서를 업로드 &#40;SharePoint 모드에서 Reporting Services&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f07cd-129">[Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="f07cd-130">[SharePoint 통합 모드에서 공유 데이터 원본 &#40;Reporting Services 만들기 및 관리&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f07cd-130">[Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="f07cd-131">[공유 데이터 원본 &#40;보고서 관리자 만들기, 삭제 또는 수정&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f07cd-131">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="f07cd-132">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f07cd-132">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="f07cd-133">Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="f07cd-133">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
