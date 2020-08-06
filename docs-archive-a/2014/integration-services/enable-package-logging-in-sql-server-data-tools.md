---
title: SQL Server Data Tools에서 패키지 로깅 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], enabling
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73dbca034047e853669dd503a62e105d1dd7b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651810"
---
# <a name="enable-package-logging-in-sql-server-data-tools"></a><span data-ttu-id="be69a-102">SQL Server Data Tools에서 패키지 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="be69a-102">Enable Package Logging in SQL Server Data Tools</span></span>
  <span data-ttu-id="be69a-103">이 절차에서는 패키지에 로그를 추가하는 방법, 패키지 수준 로깅을 구성하는 방법 및 로깅 구성을 XML 파일에 저장하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-103">This procedure describes how to add logs to a package, configure package-level logging, and save the logging configuration to an XML file.</span></span> <span data-ttu-id="be69a-104">로그는 패키지 수준에서만 추가할 수 있지만 패키지에 포함되는 컨테이너에서 로깅을 활성화하기 위해 패키지가 로깅을 수행할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-104">You can add logs only at the package level, but the package does not have to perform logging to enable logging in the containers that the package includes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be69a-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 배포하는 경우 패키지 실행에 대해 설정한 로깅 수준에 따라 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 사용하여 구성하는 패키지 로깅이 재정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-105">If you deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the logging level that you set for the package execution overrides the package logging that you configure using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="be69a-106">기본적으로 패키지 내의 컨테이너는 부모 컨테이너와 동일한 로깅 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-106">By default, the containers in the package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="be69a-107">개별 컨테이너에 대한 로깅 옵션을 설정하는 방법은 [저장된 구성 파일을 사용하여 로깅 구성](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be69a-107">For information about setting logging options for individual containers, see [Configure Logging by Using a Saved Configuration File](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md).</span></span>  
  
### <a name="to-enable-logging-in-a-package"></a><span data-ttu-id="be69a-108">패키지에 로깅을 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="be69a-108">To enable logging in a package</span></span>  
  
1.  <span data-ttu-id="be69a-109">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-109">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="be69a-110">**SSIS** 메뉴에서 **로깅**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-110">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="be69a-111">**공급자 유형** 목록에서 로그 공급자를 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-111">Select a log provider in the **Provider type** list, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="be69a-112">**구성** 열에서 연결 관리자를 선택하거나 **\<New connection>** 을 클릭하여 로그 공급자에 대한 적절한 유형의 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-112">In the **Configuration** column, select a connection manager or click **\<New connection>** to create a new connection manager of the appropriate type for the log provider.</span></span> <span data-ttu-id="be69a-113">선택한 공급자에 따라 다음 연결 관리자 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-113">Depending on the selected provider, use one of the following connection managers:</span></span>  
  
    -   <span data-ttu-id="be69a-114">텍스트 파일에는 파일 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-114">For Text files, use a File connection manager.</span></span> <span data-ttu-id="be69a-115">자세한 내용은 [File Connection Manager](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="be69a-115">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
    -   <span data-ttu-id="be69a-116">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]에는 파일 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-116">For [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use a File connection manager.</span></span>  
  
    -   <span data-ttu-id="be69a-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에는 OLE DB 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-117">For [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use an OLE DB connection manager.</span></span> <span data-ttu-id="be69a-118">자세한 내용은 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be69a-118">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
    -   <span data-ttu-id="be69a-119">Windows 이벤트 로그에는 아무 것도 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="be69a-119">For Windows Event Log, do nothing.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="be69a-120">에서 자동으로 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-120">automatically creates the log.</span></span>  
  
    -   <span data-ttu-id="be69a-121">XML 파일에는 파일 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-121">For XML files, use a File connection manager.</span></span>  
  
5.  <span data-ttu-id="be69a-122">패키지에서 사용할 각 로그에 대해 3단계 및 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-122">Repeat steps 3 and 4 for each log to use in the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be69a-123">패키지는 각 유형의 로그를 두 개 이상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-123">A package can use more than one log of each type.</span></span>  
  
6.  <span data-ttu-id="be69a-124">필요에 따라 패키지 수준 확인란을 선택하고 패키지 수준 로깅에서 사용할 로그를 선택한 다음 **세부 정보** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-124">Optionally, select the package-level check box, select the logs to use for package-level logging, and then click the **Details** tab.</span></span>  
  
7.  <span data-ttu-id="be69a-125">**자세히** 탭에서 **이벤트** 를 선택하여 모든 로그 항목을 로깅하거나 **이벤트** 선택을 취소하여 개별 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-125">On the **Details** tab, select **Events** to log all log entries, or clear **Events** to select individual events.</span></span>  
  
8.  <span data-ttu-id="be69a-126">필요에 따라 **고급** 을 클릭하여 로깅할 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-126">Optionally, click **Advanced** to specify which information to log.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be69a-127">기본적으로 모든 정보가 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-127">By default, all information is logged.</span></span>  
  
9. <span data-ttu-id="be69a-128">**세부 정보** 탭에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-128">On the **Details** tab, click **Save.**</span></span> <span data-ttu-id="be69a-129">**다른 이름으로 저장** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-129">The **Save As** dialog box appears.</span></span> <span data-ttu-id="be69a-130">로깅 구성을 저장할 폴더를 찾고 새 로그 구성의 파일 이름을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-130">Locate the folder in which to save the logging configuration, type a file name for the new log configuration, and then click **Save**.</span></span>  
  
10. <span data-ttu-id="be69a-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-131">Click **OK**.</span></span>  
  
11. <span data-ttu-id="be69a-132">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be69a-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be69a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be69a-133">See Also</span></span>  
 <span data-ttu-id="be69a-134">[Integration Services &#40;SSIS&#41; 로깅](performance/integration-services-ssis-logging.md) </span><span class="sxs-lookup"><span data-stu-id="be69a-134">[Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md) </span></span>  
 [<span data-ttu-id="be69a-135">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="be69a-135">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
