---
title: 보고서 파트 문제 해결 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9fe1932-46e7-421b-a8a9-4c54d9576e94
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 798bb59fc2470dedd3bdc5c996b4da395e57bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732312"
---
# <a name="troubleshoot-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="856e1-102">보고서 파트 문제 해결(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="856e1-102">Troubleshoot Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="856e1-103">다음은 보고서 파트로 작업할 때 도움이 되는 정보입니다</span><span class="sxs-lookup"><span data-stu-id="856e1-103">These tips can help when working with report parts.</span></span>  
  
## <a name="why-do-my-co-worker-and-i-see-different-instances-of-the-same-report-part-when-we-search-for-it"></a><span data-ttu-id="856e1-104">사용자와 사용자의 동료가 보고서 파트를 검색할 때 동일한 보고서 파트의 서로 다른 인스턴스가 표시되는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="856e1-104">Why do my co-worker and I see different instances of the same report part when we search for it?</span></span>  
 <span data-ttu-id="856e1-105">보고서 서버 또는 보고서 서버와 통합된 SharePoint 사이트에는 단일 보고서 파트의 여러 인스턴스가 있을 수 있으며, 이 경우 모든 인스턴스의 GUID(Globally Unique Identifier)는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-105">There can be multiple instances of a single report part on a report server or SharePoint site integrated with a report server, and all instances will have the same globally unique identifier (GUID).</span></span> <span data-ttu-id="856e1-106">최신 인스턴스만 검색 결과의 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-106">Only the most recent instance is displayed in the list of search results.</span></span> <span data-ttu-id="856e1-107">단일 보고서 파트의 여러 인스턴스에 대한 사용 권한이 서로 다른 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-107">In some situations, different instances of a single report part can have different permissions.</span></span> <span data-ttu-id="856e1-108">사용자와 사용자의 동료가 서버에서 서로 다른 사용 권한을 갖고 있는 경우 동일한 인스턴스를 보지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-108">If your co-worker and you have different permissions on the server, you will not see the same instance.</span></span> <span data-ttu-id="856e1-109">예를 들어 모두 GUID가 같은 보고서 파트의 여러 복사본을 SharePoint 통합 모드에서 보고서 서버의 각각 다른 폴더에 저장하는 경우</span><span class="sxs-lookup"><span data-stu-id="856e1-109">For example, say that multiple copies of a report part, all with the same GUID, are saved in different folders on a report server in SharePoint integrated mode.</span></span> <span data-ttu-id="856e1-110">이들 폴더의 사용 권한이 다르면 해당 폴더에 있는 보고서 파트의 사용 권한도 각각 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-110">If the folders have different permissions, then the report parts in those folders will also have different permissions.</span></span>  
  
 <span data-ttu-id="856e1-111">사용자와 사용자의 동료가 갖고 있는 사용 권한을 보려면 보고서 서버 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="856e1-111">To see what permissions you and your co-worker have, ask your report server administrator.</span></span>  
  
## <a name="when-i-search-for-report-parts-that-i-uploaded-to-a-sharepoint-server-i-do-not-see-them-why-not"></a><span data-ttu-id="856e1-112">SharePoint 서버로 업로드한 보고서 파트가 검색되지 않는</span><span class="sxs-lookup"><span data-stu-id="856e1-112">When I search for report parts that I uploaded to a SharePoint server, I do not see them.</span></span> <span data-ttu-id="856e1-113">이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="856e1-113">Why not?</span></span>  
 <span data-ttu-id="856e1-114">보고서 작성기를 사용하여 게시하는 대신 SharePoint 문서 라이브러리로 수동 업로드한 보고서 파트는 보고서 파트 갤러리에 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-114">Report Parts that you have manually uploaded to a SharePoint document library, instead of published by using Report Builder, might not appear in the Report Part Gallery.</span></span> <span data-ttu-id="856e1-115">갤러리 검색에 사용되는 보고서 서버를 SharePoint 문서 라이브러리의 내용과 동기화해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-115">The report server used for the gallery search might need to be synchronized with the contents of the SharePoint document library.</span></span> <span data-ttu-id="856e1-116">자세한 내용은 msdn.microsoft.com의 온라인 설명서에서 [SharePoint 중앙 관리의 보고서 서버 파일 동기화 기능 활성화](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) 를 참조 하세요 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) .</span><span class="sxs-lookup"><span data-stu-id="856e1-116">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
## <a name="why-cant-others-see-the-image-in-their-reports"></a><span data-ttu-id="856e1-117">다른 사용자가 자신의 보고서에서 이미지를 볼 수 없는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="856e1-117">Why can't others see the image in their reports?</span></span>  
 <span data-ttu-id="856e1-118">이미지 파일에 대한 링크인 보고서 파트를 게시하는 경우 해당 보고서 파트는 실제로 링크일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-118">If you publish a report part that is a link to an image file, the report part is really just a link.</span></span> <span data-ttu-id="856e1-119">다른 사용자가 이미지 보고서 파트를 자신의 보고서에 추가할 때 이미지를 볼 수 없는 경우 연결되어 있는 이미지에 대한 사용 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-119">If others cannot see the image when they add the image report part to their reports, they might not have permissions for the image that you are linking to.</span></span>  
  
 <span data-ttu-id="856e1-120">이 문제를 해결할 수 있는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-120">There are a few possible solutions to this:</span></span>  
  
-   <span data-ttu-id="856e1-121">이미지 파일에 대한 링크를 보고서 파트로 만드는 대신 이미지 파일을 보고서 파트로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-121">Make the image file a report part, instead of making the link to the image file the report part.</span></span>  
  
-   <span data-ttu-id="856e1-122">이미지 파일을 다른 사용자가 사용 권한을 가진 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-122">Move the image file to a location for which others have permissions.</span></span>  
  
-   <span data-ttu-id="856e1-123">사용 권한을 변경하려면 보고서 서버 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="856e1-123">Ask the report server administrator to change permissions.</span></span>  
  
## <a name="why-do-i-get-a-circular-reference-error-message-when-i-try-to-publish-my-report-part"></a><span data-ttu-id="856e1-124">보고서 파트를 게시하려고 하면 “순환 참조” 오류 메시지가 표시되는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="856e1-124">Why do I get a "circular reference" error message when I try to publish my report part?</span></span>  
 <span data-ttu-id="856e1-125">순환 참조가 포함된 보고서 항목은 보고서 파트로 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-125">If report items have a circular reference, you won't be able to publish them as report parts.</span></span> <span data-ttu-id="856e1-126">예를 들어 보고서 항목이 가리키는 데이터 세트이 매개 변수를 가리키고</span><span class="sxs-lookup"><span data-stu-id="856e1-126">For example, a report item points to a dataset, which in turn points to a parameter.</span></span> <span data-ttu-id="856e1-127">이 매개 변수가 데이터 세트을 다시 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-127">The parameter, in turn, points to the dataset¸ too.</span></span> <span data-ttu-id="856e1-128">이 경우에는 참조 중 하나를 삭제해야 보고서 파트를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="856e1-128">You'll need to delete one of the references first before you can publish the report part.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856e1-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="856e1-129">See Also</span></span>  
 [<span data-ttu-id="856e1-130">보고서 파트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="856e1-130">Report Parts &#40;Report Builder and SSRS&#41;</span></span>](report-parts-report-builder-and-ssrs.md)  
  
  
