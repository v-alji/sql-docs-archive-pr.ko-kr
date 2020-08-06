---
title: 저장 된 구성 파일을 사용 하 여 로깅 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- logs [Integration Services], containers
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8eb517462d9e932906f739678fbd46c1004fb84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652270"
---
# <a name="configure-logging-by-using-a-saved-configuration-file"></a><span data-ttu-id="5babe-102">저장된 구성 파일을 사용하여 로깅 구성</span><span class="sxs-lookup"><span data-stu-id="5babe-102">Configure Logging by Using a Saved Configuration File</span></span>
  <span data-ttu-id="5babe-103">이 절차에서는 이전에 저장된 로깅 구성 파일을 로드하여 패키지 내의 새 컨테이너를 위한 로깅을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-103">This procedure describes how to configure logging for new containers in a package by loading a previously saved logging configuration file.</span></span>  
  
 <span data-ttu-id="5babe-104">기본적으로 패키지의 모든 컨테이너는 부모 컨테이너와 동일한 로깅 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-104">By default, all containers in a package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="5babe-105">예를 들어 Foreach 루프 내의 태스크는 Foreach 루프와 동일한 로깅 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-105">For example, the tasks in a Foreach Loop use the same logging configuration as the Foreach Loop.</span></span>  
  
### <a name="to-configure-logging-for-a-container"></a><span data-ttu-id="5babe-106">컨테이너에 대한 로깅을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="5babe-106">To configure logging for a container</span></span>  
  
1.  <span data-ttu-id="5babe-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="5babe-108">**SSIS** 메뉴에서 **로깅**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-108">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="5babe-109">패키지 트리 뷰를 확장하고 구성할 컨테이너를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-109">Expand the package tree view and select the container to configure.</span></span>  
  
4.  <span data-ttu-id="5babe-110">**공급자 및 로그** 탭에서 컨테이너로 사용할 로그를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-110">On the **Providers and Logs** tab, select the logs to use for the container.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5babe-111">패키지 수준에서만 로그를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-111">You can create logs only at the package level.</span></span> <span data-ttu-id="5babe-112">자세한 내용은 [SQL Server Data Tools에서 패키지 로깅 사용](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5babe-112">For more information, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
5.  <span data-ttu-id="5babe-113">**자세히** 탭을 클릭하고 **로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-113">Click the **Details** tab and click **Load**.</span></span>  
  
6.  <span data-ttu-id="5babe-114">사용할 로깅 구성 파일을 찾고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-114">Locate the logging configuration file you want to use and click **Open**.</span></span>  
  
7.  <span data-ttu-id="5babe-115">필요에 따라 **이벤트** 열에서 해당 확인란을 선택하여 기록할 다른 로그 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-115">Optionally, select a different log entry to log by selecting its check box in the **Events** column.</span></span> <span data-ttu-id="5babe-116">**고급** 을 클릭하여 이 항목에 대해 기록할 정보 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-116">Click **Advanced** to select the type of information to log for this entry.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5babe-117">새 컨테이너는 원래 로깅 구성을 만드는 데 사용된 컨테이너에는 사용할 수 없는 추가 로그 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-117">The new container may include additional log entries that are not available for the container originally used to create the logging configuration.</span></span> <span data-ttu-id="5babe-118">이러한 추가 로그 항목을 로그하려면 수동으로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-118">These additional log entries must be selected manually if you want them to be logged.</span></span>  
  
8.  <span data-ttu-id="5babe-119">로깅 구성의 업데이트된 버전을 저장하려면 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-119">To save the updated version of the logging configuration, click **Save**.</span></span>  
  
9. <span data-ttu-id="5babe-120">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5babe-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5babe-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5babe-121">See Also</span></span>  
 [<span data-ttu-id="5babe-122">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="5babe-122">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
