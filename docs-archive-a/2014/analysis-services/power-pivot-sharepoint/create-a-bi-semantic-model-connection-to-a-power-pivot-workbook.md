---
title: PowerPivot 통합 문서에 대 한 BI 의미 체계 모델 연결 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e3f97f-18a8-42b6-9030-b4f818afc3b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ea4ddcc38328acc6ff8cfb5387b13056b689a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653575"
---
# <a name="create-a-bi-semantic-model-connection-to-a-powerpivot-workbook"></a><span data-ttu-id="eb53b-102">PowerPivot 통합 문서에 대한 BI 의미 체계 모델 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="eb53b-102">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>
  <span data-ttu-id="eb53b-103">동일한 팜의 PowerPivot 통합 문서로 리디렉션하는 BI 의미 체계 모델 연결을 설정하려면 이 항목의 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-103">Use the information in this topic to set up a BI semantic model connection that redirects to a PowerPivot workbook in the same farm.</span></span>  
  
 <span data-ttu-id="eb53b-104">BI 의미 체계 모델 연결을 만들고 SharePoint 사용 권한을 구성한 후에는 이 연결을 Excel 또는 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 보고서에 데이터 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-104">After you create a BI semantic model connection and configure SharePoint permissions, you can use it as a data source for Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span>  
  
 <span data-ttu-id="eb53b-105">이 항목은 다음과 같은 섹션으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-105">This topic includes the following sections.</span></span> <span data-ttu-id="eb53b-106">지정된 순서로 각 태스크를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="eb53b-106">Perform each task in the order given.</span></span>  
  
 [<span data-ttu-id="eb53b-107">필수 구성 요소 검토</span><span class="sxs-lookup"><span data-stu-id="eb53b-107">Review Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="eb53b-108">연결 만들기</span><span class="sxs-lookup"><span data-stu-id="eb53b-108">Create a Connection</span></span>](#bkmk_create)  
  
 [<span data-ttu-id="eb53b-109">BI 의미 체계 모델 연결에 대한 SharePoint 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="eb53b-109">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>](#bkmk_permissions)  
  
 [<span data-ttu-id="eb53b-110">통합 문서에 대한 SharePoint 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="eb53b-110">Configure SharePoint Permissions on the Workbook</span></span>](#bkmk_userdb)  
  
 [<span data-ttu-id="eb53b-111">다음 단계</span><span class="sxs-lookup"><span data-stu-id="eb53b-111">Next Steps</span></span>](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="eb53b-112">필수 조건 검토</span><span class="sxs-lookup"><span data-stu-id="eb53b-112">Review Prerequisites</span></span>  
 <span data-ttu-id="eb53b-113">BI 의미 체계 모델 연결 파일을 만들려면 참가 권한 이상이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-113">You must have Contribute permissions or above to create a BI semantic model connection file.</span></span>  
  
 <span data-ttu-id="eb53b-114">BI 의미 체계 모델 연결 콘텐츠 형식을 지원하는 라이브러리가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-114">You must have a library that supports the BI semantic model connection content type.</span></span> <span data-ttu-id="eb53b-115">자세한 내용은 [라이브러리에 BI 의미 체계 모델 연결 콘텐츠 형식 추가 &#40;SharePoint용 PowerPivot&#41;](add-bi-semantic-model-connection-content-type-to-library.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eb53b-115">For more information, see [Add a BI Semantic Model Connection Content Type to a Library &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).</span></span>  
  
 <span data-ttu-id="eb53b-116">BI 의미 체계 모델 연결을 설정할 PowerPivot 통합 문서의 URL (예: http://adventure-works/shared documents/myworkbook.xlsx)을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-116">You must know the URL of the PowerPivot workbook for which you are setting up a BI semantic model connection (for example, http://adventure-works/shared documents/myworkbook.xlsx).</span></span> <span data-ttu-id="eb53b-117">통합 문서는 동일한 팜에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-117">The workbook must be in the same farm.</span></span>  
  
 <span data-ttu-id="eb53b-118">연결 시퀀스에 참가하는 모든 컴퓨터 및 사용자는 동일한 도메인이나 트러스트된 도메인(양방향 신뢰)에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-118">All computers and users that participate in the connection sequence must be in the same domain or trusted domain (two-way trust).</span></span>  
  
##  <a name="create-a-connection"></a><a name="bkmk_create"></a><span data-ttu-id="eb53b-119">연결 만들기</span><span class="sxs-lookup"><span data-stu-id="eb53b-119">Create a Connection</span></span>  
  
1.  <span data-ttu-id="eb53b-120">BI 의미 체계 모델 연결이 포함될 라이브러리의 SharePoint 리본에서 **문서** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-120">In the library that will contain the BI semantic model connection, click **Documents** on the SharePoint ribbon.</span></span> <span data-ttu-id="eb53b-121">새 문서에서 아래쪽 화살표를 클릭하고 **BISM 연결 파일** 을 선택하여 새 BI 의미 체계 모델 연결 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-121">Click the down arrow on New Document, and select **BISM Connection File** to open the New BI Semantic Model Connection page.</span></span>  
  
     <span data-ttu-id="eb53b-122">![SharePoint 라이브러리의 새 문서 하위 메뉴](../media/ssas-bismconnection-new.gif "SharePoint 라이브러리의 새 문서 하위 메뉴")</span><span class="sxs-lookup"><span data-stu-id="eb53b-122">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
2.  <span data-ttu-id="eb53b-123">**서버** 속성을 PowerPivot 통합 문서의 SharePoint URL (예: \*\* http://mysharepoint/shared documents/myWorkbook.xlsx\*\*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-123">Set the **Server** property to the SharePoint URL of the PowerPivot workbook (for example, **http://mysharepoint/shared documents/myWorkbook.xlsx**.</span></span> <span data-ttu-id="eb53b-124">SharePoint용 PowerPivot 배포에서는 팜의 모든 서버에 데이터가 로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-124">In a PowerPivot for SharePoint deployment, data can be loaded on any server in the farm.</span></span> <span data-ttu-id="eb53b-125">이러한 이유로 PowerPivot 데이터에 대한 데이터 원본 연결은 통합 문서의 경로만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-125">For this reason, data source connections to PowerPivot data specify just the path to the workbook.</span></span> <span data-ttu-id="eb53b-126">데이터를 로드하는 서버는 PowerPivot 시스템 서비스에서 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-126">The PowerPivot System Service determines which server loads the data.</span></span>  
  
     <span data-ttu-id="eb53b-127">**데이터베이스** 속성을 사용 하지 마십시오. PowerPivot 통합 문서의 위치를 지정 하는 경우에는 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-127">Do not use the **Database** property; it is not used when specifying the location of a PowerPivot workbook.</span></span>  
  
     <span data-ttu-id="eb53b-128">페이지는 다음 그림과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-128">Your page should look similar to the following illustration.</span></span>  
  
     <span data-ttu-id="eb53b-129">![통합 문서에 대한 URL을 보여 주는 BISM 연결 페이지](../media/ssas-bismconnection-ppvtds.gif "통합 문서에 대한 URL을 보여 주는 BISM 연결 페이지")</span><span class="sxs-lookup"><span data-stu-id="eb53b-129">![BISM connection page showing URL to workbook](../media/ssas-bismconnection-ppvtds.gif "BISM connection page showing URL to workbook")</span></span>  
  
     <span data-ttu-id="eb53b-130">통합 문서에 대한 SharePoint 사용 권한이 있는 경우 추가 유효성 검사 단계도 수행하여 위치가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-130">Optionally, if you have SharePoint permissions to the workbook, an extra validation step is performed, ensuring that the location is valid.</span></span> <span data-ttu-id="eb53b-131">데이터에 액세스할 권한이 없는 경우 유효성 검사 응답 없이 BI 의미 체계 모델 연결을 저장할 수 있는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-131">If you do not have permission to access the data, you are given the option of saving the BI semantic model connection without the validation response.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a><span data-ttu-id="eb53b-132">BI 의미 체계 모델 연결에 대 한 SharePoint 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="eb53b-132">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>  
 <span data-ttu-id="eb53b-133">BI 의미 체계 모델 연결을 Excel 통합 문서 또는 Reporting Services 보고서의 데이터 원본으로 사용하려면 SharePoint 라이브러리의 BI 의미 체계 모델 연결 항목에 대해 **읽기** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-133">Ability to use a BI semantic model connection as a data source for an Excel workbook or Reporting Services report requires **Read** permissions on the BI semantic model connection item in a SharePoint library.</span></span> <span data-ttu-id="eb53b-134">읽기 권한 수준에는 BI 의미 체계 모델 연결 정보를 Excel 데스크톱 애플리케이션에 다운로드할 수 있는 **항목 열기** 권한이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-134">The Read permission level includes the **Open Items** permission that enables downloading BI semantic model connection information to an Excel desktop application.</span></span>  
  
 <span data-ttu-id="eb53b-135">여러 가지 방법으로 SharePoint에서 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-135">There are several ways to grant permissions in SharePoint.</span></span> <span data-ttu-id="eb53b-136">다음은 **읽기** 수준의 권한이 있는 **BISM Users** 라는 새 그룹을 만드는 방법을 설명하는 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-136">The following instructions explain how to create a new group called **BISM Users** that have the **Read** permission level.</span></span>  
  
 <span data-ttu-id="eb53b-137">사용 권한을 변경하려면 사이트 소유자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-137">You must be a site owner to change permissions.</span></span>  
  
1.  <span data-ttu-id="eb53b-138">사이트 작업에서 **사이트 사용 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-138">In Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="eb53b-139">**그룹 만들기** 를 클릭하고 새 그룹의 이름을 **BISM Users**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-139">Click **Create Group** and name the new group **BISM Users**.</span></span>  
  
3.  <span data-ttu-id="eb53b-140">**읽기** 권한 수준을 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-140">Choose the **Read** permission level and click **Create**.</span></span>  
  
4.  <span data-ttu-id="eb53b-141">사용자 및 그룹에서 **BISM Users** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-141">Select **BISM Users** in People and Groups.</span></span>  
  
5.  <span data-ttu-id="eb53b-142">새로 만들기를 가리키고 **사용자 추가**를 클릭한 다음 사용자 또는 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-142">Point to New, click **Add Users**, and then add user or group accounts.</span></span>  
  
     <span data-ttu-id="eb53b-143">이 사용자 및 그룹은 이제 사이트 수준에서 사용 권한을 상속하는 모든 라이브러리와 목록을 포함하여 사이트 전체에서 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-143">These users and groups will now have Read permissions throughout the site, including all libraries and lists that inherit permissions from the site level.</span></span> <span data-ttu-id="eb53b-144">이 사용 권한이 너무 높은 경우 특정 라이브러리, 목록 또는 항목에서 이 그룹을 선택적으로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-144">If these permissions are too high, you can selectively remove this group from specific libraries, lists, or items.</span></span>  
  
 <span data-ttu-id="eb53b-145">항목 수준에서 사용 권한을 선택적으로 제거하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-145">To selectively remove permissions at the item level, do the following:</span></span>  
  
1.  <span data-ttu-id="eb53b-146">라이브러리에서 문서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-146">In a library, select a document.</span></span> <span data-ttu-id="eb53b-147">오른쪽 아래 화살표를 클릭한 다음 **사용 권한 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-147">Click the right down arrow and then click **Manage Permissions**.</span></span>  
  
2.  <span data-ttu-id="eb53b-148">기본적으로 항목은 사용 권한을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-148">By default, an item inherits permissions.</span></span> <span data-ttu-id="eb53b-149">이 라이브러리에서 개별 문서의 사용 권한을 변경하려면 **권한 상속 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-149">To change the permissions of individual documents in this library, click **Stop Inheriting Permissions**.</span></span>  
  
3.  <span data-ttu-id="eb53b-150">**BISM Users**옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-150">Select the checkbox next to **BISM Users**.</span></span>  
  
4.  <span data-ttu-id="eb53b-151">**사용자의 사용 권한 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-151">Click **Remove User Permissions**.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-workbook"></a><a name="bkmk_userdb"></a><span data-ttu-id="eb53b-152">통합 문서에 대 한 SharePoint 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="eb53b-152">Configure SharePoint Permissions on the Workbook</span></span>  
 <span data-ttu-id="eb53b-153">Excel 통합 문서 내부에서 PowerPivot 데이터베이스를 사용하는 경우 Excel 통합 문서에 대한 SharePoint 사용 권한에 따라 BI 의미 체계 모델 연결을 통한 데이터 액세스가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-153">If you are using a PowerPivot database inside an Excel workbook, the SharePoint permissions on the Excel workbook determine data access via the BI semantic model connection.</span></span> <span data-ttu-id="eb53b-154">통합 문서를 외부 데이터 원본으로 사용하려면 통합 문서에 액세스하는 모든 사용자가 통합 문서에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-154">All users who access the workbook must have Read permissions on the workbook in order to use it as an external data source.</span></span>  
  
 <span data-ttu-id="eb53b-155">통합 문서가 상속된 사용 권한을 사용한다고 가정하면 이전 섹션의 지침을 사용하여 **BISM Users** 그룹을 만든 경우 **BISM Users** 의 멤버인 사용자 및 그룹 계정에게는 통합 문서 및 BI 의미 체계 모델 연결 파일에 대해 충분한 사용 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-155">If you created a **BISM Users** group using the instructions in the previous section, user and group accounts that are members of **BISM Users** will have sufficient permission on the workbook as well as the BI semantic model connection file, assuming the workbook uses inherited permissions.</span></span>  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a> <span data-ttu-id="eb53b-156">다음 단계</span><span class="sxs-lookup"><span data-stu-id="eb53b-156">Next Steps</span></span>  
 <span data-ttu-id="eb53b-157">BI 의미 체계 모델 연결을 만들고 확인한 후 데이터 원본으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb53b-157">After you create and secure a BI semantic model connection, you can specify it as a data source.</span></span> <span data-ttu-id="eb53b-158">자세한 내용은 [Excel 또는 Reporting Services에서 BI 의미 체계 모델 연결 사용](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eb53b-158">For more information, see [Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb53b-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb53b-159">See Also</span></span>  
 <span data-ttu-id="eb53b-160">[PowerPivot BI 의미 체계 모델 연결 &#40;. bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="eb53b-160">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 <span data-ttu-id="eb53b-161">[Excel 또는 Reporting Services에서 BI 의미 체계 모델 연결 사용](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb53b-161">[Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span></span>  
 [<span data-ttu-id="eb53b-162">Create a BI Semantic Model Connection to a Tabular Model Database</span><span class="sxs-lookup"><span data-stu-id="eb53b-162">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
  
