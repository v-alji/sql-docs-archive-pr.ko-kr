---
title: SharePoint 라이브러리에 보고서 저장(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49878a0d7115a11e804382cb5139aa0ec7b3d254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650772"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a><span data-ttu-id="b3e3d-102">SharePoint 라이브러리에 보고서 저장(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="b3e3d-102">Save a Report to a SharePoint Library (Report Builder)</span></span>
  <span data-ttu-id="b3e3d-103">SharePoint 통합용으로 구성된 보고서 서버에 보고서를 저장하려면 SharePoint 서버로 이동하여 보고서 서버에 대한 연결을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-103">To save a report to a report server configured for SharePoint integration, you must browse to the SharePoint server and establish a connection to the report server.</span></span> <span data-ttu-id="b3e3d-104">보고서 정의에서 보고서와 관련된 항목에 대한 모든 참조에는 SharePoint 보고서 서버에 맞는 값을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-104">In the report definition, all references to items related to the report must use values that are specific to a SharePoint report server.</span></span> <span data-ttu-id="b3e3d-105">관련 항목에는 하위 보고서, 드릴스루 보고서 및 웹 기반 이미지 등의 리소스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-105">Related items include subreports, drillthrough reports, and resources such as Web-based images.</span></span> <span data-ttu-id="b3e3d-106">자세한 내용은 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-106">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b3e3d-107">프로젝트의 속성을 설정하려면 SharePoint 사이트에 대한 **멤버** 또는 **소유자** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-107">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span>  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a><span data-ttu-id="b3e3d-108">SharePoint 사이트에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="b3e3d-108">To save a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="b3e3d-109">보고서 작성기 단추에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="b3e3d-110">다른 **이름으로 저장** _\<Report Item>_ 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-110">The **Save As**_\<Report Item>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b3e3d-111">보고서를 다시 저장하는 경우 보고서가 이전 위치에 자동으로 다시 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="b3e3d-112">**다른 이름으로 저장** 옵션을 사용하여 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-112">Use the **Save As** option to change location.</span></span>  
  
2.  <span data-ttu-id="b3e3d-113">필요한 경우 **최근에 사용한 사이트 및 서버** 를 클릭하여 최근에 사용한 보고서 서버와 SharePoint 사이트의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="b3e3d-114">SharePoint 사이트를 찾은 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-114">Browse to the SharePoint site, and then click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b3e3d-115">변경된 보고서를 저장하지 않은 상태로 10시간 이상 두면 저장되지 않은 상태로 서버에서 연결이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-115">If you leave a changed report for more than 10 hours without saving it, it is disconnected from the server without being saved.</span></span> <span data-ttu-id="b3e3d-116">그러면 왼쪽 아래의 상태 표시줄에서 **연결 끊기**를 클릭한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-116">If that happens, in the lower-right status bar, click **Disconnect**, and then click **Connect**.</span></span> <span data-ttu-id="b3e3d-117">최신 서버는 사용 가능한 서버 목록에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-117">The most recent server will be in the list of available servers.</span></span> <span data-ttu-id="b3e3d-118">서버를 선택하면 보고서가 다시 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e3d-118">Select it and the report will reconnect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e3d-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3e3d-119">See Also</span></span>  
 [<span data-ttu-id="b3e3d-120">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b3e3d-120">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
