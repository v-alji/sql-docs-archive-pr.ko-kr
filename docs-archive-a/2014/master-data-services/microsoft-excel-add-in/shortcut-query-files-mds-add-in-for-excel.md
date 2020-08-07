---
title: 바로 가기 쿼리 파일(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe1bdbdadabe0e6448ed3bdc65316104fb26ba43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730788"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a><span data-ttu-id="ea7f2-102">바로 가기 쿼리 파일(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="ea7f2-102">Shortcut Query Files (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="ea7f2-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 바로 가기 쿼리 파일을 사용하여 자주 사용되는 데이터를 신속하게 연결하고 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use shortcut query files to quickly connect and load frequently-used data.</span></span> <span data-ttu-id="ea7f2-104">또한 다른 사용자와 MDS 데이터를 공유할 때에도 이를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-104">You can also use them when you want to share MDS data with others.</span></span> <span data-ttu-id="ea7f2-105">워크시트를 저장하고 전자 메일로 전송하는 대신 바로 가기 쿼리 파일을 저장하고 이 파일을 대신 전자 메일로 전송해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-105">Instead of saving the worksheet and emailing it, you should save a shortcut query file and email that instead.</span></span> <span data-ttu-id="ea7f2-106">이렇게 하면 MDS 저장소에 연결하여 최신 파일을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-106">This ensures that you are both connecting to the MDS repository to get the latest data.</span></span>  
  
 <span data-ttu-id="ea7f2-107">바로 가기 쿼리 파일은 다음에 대한 정보가 포함된 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-107">Shortcut query files are XML files that contain information about:</span></span>  
  
-   <span data-ttu-id="ea7f2-108">MDS 저장소 연결</span><span class="sxs-lookup"><span data-stu-id="ea7f2-108">The MDS repository connection.</span></span>  
  
-   <span data-ttu-id="ea7f2-109">모델, 버전 및 엔터티</span><span class="sxs-lookup"><span data-stu-id="ea7f2-109">The model, version, and entity.</span></span>  
  
-   <span data-ttu-id="ea7f2-110">바로 가기를 만들 때 적용된 모든 필터</span><span class="sxs-lookup"><span data-stu-id="ea7f2-110">Any filters that were applied when the shortcut was created.</span></span>  
  
-   <span data-ttu-id="ea7f2-111">바로 가기를 만들 때 왼쪽에서 오른쪽으로의 열 순서</span><span class="sxs-lookup"><span data-stu-id="ea7f2-111">The left-to-right order of the columns when the shortcut was created.</span></span>  
  
 <span data-ttu-id="ea7f2-112">이러한 파일을 목록에 저장하여 추가 기능을 열 때 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-112">You can save these files in a list and choose from them when you open the Add-in.</span></span> <span data-ttu-id="ea7f2-113">이를 컴퓨터 또는 공유 위치에 내보내거나 다른 사용자에게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-113">You can export them to your computer or to a shared location, or you can send them to others.</span></span>  
  
## <a name="queryopener-application"></a><span data-ttu-id="ea7f2-114">QueryOpener 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="ea7f2-114">QueryOpener Application</span></span>  
 <span data-ttu-id="ea7f2-115">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 을 설치한 모든 사용자에게는 QueryOpener라는 애플리케이션이 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-115">All users who install the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] have an application called QueryOpener installed.</span></span> <span data-ttu-id="ea7f2-116">이 애플리케이션은 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 바로 가기 쿼리 파일을 여는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-116">This application is used to open shortcut query files in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)].</span></span> <span data-ttu-id="ea7f2-117">바로 가기 쿼리 파일을 두 번 클릭하면 이 애플리케이션이 추가 기능에서 파일을 여는 데 자동으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-117">If you double-click a shortcut query file, this application is automatically used to open the file in the Add-in.</span></span>  
  
 <span data-ttu-id="ea7f2-118">이 애플리케이션에서 바로 가기 쿼리 파일을 열면 해당 연결을 "안전한" 연결 즉, 이 위치의 콘텐츠를 신뢰할 수 있는 연결로 지정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-118">When you open a shortcut query file with this application, you are prompted to make the connection a "safe" connection, which means you trust content from this location.</span></span> <span data-ttu-id="ea7f2-119">연결을 안전한 연결로 표시할 때마다 연결이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-119">Each time you mark a connection as safe, it is added to a list.</span></span> <span data-ttu-id="ea7f2-120">이 목록을 지우려면 **설정** 대화 상자를 열고 **수신 허용 목록에 추가된 서버** 섹션에서 **모두 지우기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-120">If you want to clear this list, open the **Settings** dialog box and in the **Servers Added to Safe List** section, click **Clear All**.</span></span>  
  
 <span data-ttu-id="ea7f2-121">응용 프로그램의 기본 위치는 *drive*: Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe입니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-121">The default location for the application is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.</span></span>  
  
 <span data-ttu-id="ea7f2-122">다음 두 가지 방법으로 바로 가기 쿼리 파일을 열 수 있습니다. 가져오거나 두 번 클릭 하면 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-122">There are two ways to open shortcut query files: you can import them or you can double-click them and they are opened automatically.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ea7f2-123">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ea7f2-123">Related Tasks</span></span>  
  
|<span data-ttu-id="ea7f2-124">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="ea7f2-124">Task Description</span></span>|<span data-ttu-id="ea7f2-125">항목</span><span class="sxs-lookup"><span data-stu-id="ea7f2-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ea7f2-126">활성 워크시트의 내용을 바로 가기 쿼리 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-126">Save the contents of the active worksheet as a shortcut query file.</span></span>|[<span data-ttu-id="ea7f2-127">바로 가기 쿼리 파일 저장&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="ea7f2-127">Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|<span data-ttu-id="ea7f2-128">활성 워크시트의 내용을 제공하는 바로 가기 쿼리 파일을 전자 메일로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="ea7f2-128">Email a shortcut query file that represents the contents of the active worksheet.</span></span>|[<span data-ttu-id="ea7f2-129">바로 가기 쿼리 파일을 메일로 보내기&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="ea7f2-129">Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="ea7f2-130">관련 내용</span><span class="sxs-lookup"><span data-stu-id="ea7f2-130">Related Content</span></span>  
  
-   [<span data-ttu-id="ea7f2-131">연결&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="ea7f2-131">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="ea7f2-132">Microsoft Excel용 Master Data Services 추가 기능</span><span class="sxs-lookup"><span data-stu-id="ea7f2-132">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="ea7f2-133">보안&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ea7f2-133">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
