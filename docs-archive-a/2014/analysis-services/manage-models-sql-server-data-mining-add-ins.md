---
title: 모델 관리 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f4b5961ec79bb949bf7fa5f53a980f066e81379
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653629"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a><span data-ttu-id="4a880-102">모델 관리(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="4a880-102">Manage Models (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="4a880-103">![데이터 마이닝 리본, 모델 관리 단추](media/dmc-manage.gif "데이터 마이닝 리본, 모델 관리 단추")</span><span class="sxs-lookup"><span data-stu-id="4a880-103">![Manage Models button, Data Mining ribbon](media/dmc-manage.gif "Manage Models button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="4a880-104">**모델 관리** 대화 상자를 사용 하면 현재 연결 되어 있는 서버에 저장 된 기존 마이닝 모델 및 마이닝 구조와 상호 작용할 수 있습니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4a880-104">The **Manage Models** dialog box enables you to interact with existing mining models and mining structures that are stored in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server to which you are currently connected.</span></span> <span data-ttu-id="4a880-105">또한 현재 세션 중에 만든 임시 구조 및 모델을 보고 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-105">You can also view and manage temporary structures and models that have been created during the current session.</span></span> <span data-ttu-id="4a880-106">세션 모델 및 서버에 저장된 모델을 모두 사용한 경우 둘 다 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-106">If you have used both session models and models stored on a server, both are visible in the dialog box.</span></span>  
  
## <a name="using-the-manage-models-wizard"></a><span data-ttu-id="4a880-107">모델 관리 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="4a880-107">Using the Manage Models Wizard</span></span>  
 <span data-ttu-id="4a880-108">**모델 관리**를 클릭 하면 기존 데이터 마이닝 모델 및 구조를 관리 하는 다음 기능에 대 한 액세스를 제공 하는 **마이닝 구조 및 모델 관리** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-108">When you click **Manage Models**, the **Manage Mining Structures and Models** dialog box opens, providing access to the following functionality for managing existing data mining models and structures:</span></span>  
  
-   <span data-ttu-id="4a880-109">마이닝 모델 또는 구조 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="4a880-109">Rename a mining model or structure</span></span>  
  
-   <span data-ttu-id="4a880-110">마이닝 모델 또는 구조 삭제</span><span class="sxs-lookup"><span data-stu-id="4a880-110">Delete a mining model or structure</span></span>  
  
-   <span data-ttu-id="4a880-111">마이닝 모델 또는 구조 지우기</span><span class="sxs-lookup"><span data-stu-id="4a880-111">Clear a mining model or structure</span></span>  
  
-   <span data-ttu-id="4a880-112">새 데이터 또는 기존 데이터를 사용하여 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="4a880-112">Process a mining structure, using either new or existing data</span></span>  
  
-   <span data-ttu-id="4a880-113">마이닝 모델 또는 구조 내보내기 또는 가져오기</span><span class="sxs-lookup"><span data-stu-id="4a880-113">Export or import a mining model or structure</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a880-114">이 대화 상자를 사용하여 쿼리 또는 모델을 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-114">You cannot create queries or models by using this dialog box.</span></span> <span data-ttu-id="4a880-115">새 마이닝 구조를 만들려면 Excel 용 데이터 마이닝 클라이언트에서 제공 하는 마법사 중 하나를 사용 하거나 **데이터 마이닝 쿼리 고급 편집기**를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-115">To create a new mining structure, use one of the wizards provided in the Data Mining Client for Excel, or use the **Data Mining Query Advanced Editor**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="4a880-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4a880-116">Requirements</span></span>  
 <span data-ttu-id="4a880-117">데이터 마이닝 모델을 관리하려면 먼저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-117">To manage data mining models, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4a880-118">임시 파일에 저장된 세션 모델을 사용하는 경우에도 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-118">A connection is required even if you are working with session models stored in a temporary file.</span></span> <span data-ttu-id="4a880-119">연결을 만들거나 변경 하는 방법에 대 한 자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4a880-119">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="4a880-120">연결하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 기존 데이터 마이닝 구조 또는 데이터 마이닝 모델이 없는 경우 이 추가 기능에서 제공하는 마법사 및 다른 도구를 사용하여 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-120">If the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you connect to does not contain any existing data mining structures or data mining models, you can create them by using the wizards and other tools provided by this add-in.</span></span> <span data-ttu-id="4a880-121">**고급 편집기 데이터 마이닝 모델**을 사용 하 여 새 모델을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a880-121">You can also create new models by using the **Data Mining Model Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a880-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a880-122">See Also</span></span>  
 <span data-ttu-id="4a880-123">[Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 문서화&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="4a880-123">[Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="4a880-124">Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="4a880-124">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
