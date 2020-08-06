---
title: MDSModelDeploy를 사용하여 모델 배포 패키지 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c546d6398234dd43103d0e6c75822377e11de61a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661218"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="920c4-102">MDSModelDeploy를 사용하여 모델 배포 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="920c4-102">Create a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="920c4-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 MDSModelDeploy 도구를 사용하여 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to create a package.</span></span> <span data-ttu-id="920c4-104">지정한 명령에 따라 패키지는 다음 중 하나를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-104">Depending on the commands you specify, the package can contain either:</span></span>  
  
-   <span data-ttu-id="920c4-105">모델 개체만</span><span class="sxs-lookup"><span data-stu-id="920c4-105">Model objects only.</span></span>  
  
-   <span data-ttu-id="920c4-106">모델 개체 및 데이터</span><span class="sxs-lookup"><span data-stu-id="920c4-106">Model objects and data.</span></span>  
  
 <span data-ttu-id="920c4-107">모델 개체만 포함하는 패키지를 배포하려면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 모델 배포 마법사를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-107">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="920c4-108">자세한 내용은 [마법사를 사용하여 모델 배포 패키지 만들기](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="920c4-108">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
> [!NOTE]  
> <span data-ttu-id="920c4-109">이 버전의 MDSModelDeploy 도구는 GB 이상의 메모리를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-109">This version of the MDSModelDeploy tool cannot use more than gigabytes (GB) of memory.</span></span> <span data-ttu-id="920c4-110">**모델 개체 및 데이터** 옵션을 사용 하 여 대량 모델을 만들거나 배포할 때 "메모리 부족" 또는 "스트림이 너무 깁니다" 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-110">When you create or deploy large models by using **Model objects and data** option, you may experience "Out of Memory" or "Stream was too long" errors.</span></span> <span data-ttu-id="920c4-111">이 문제를 해결 하려면 MDS 준비를 사용 하 여 데이터를 배포 합니다. 또는 업데이트 된 버전의 MDSModelDeploy 도구를 포함 하는 MDS 2016 이상 버전으로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-111">To resolve this issue, use MDS staging to deploy the data; or upgrade to MDS 2016 or a later version, which includes the updated version of the MDSModelDeploy tool.</span></span>
## <a name="prerequisites"></a><span data-ttu-id="920c4-112">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="920c4-112">Prerequisites</span></span>  
 <span data-ttu-id="920c4-113">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="920c4-113">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="920c4-114">MDSModelDeploy 도구를 실행하는 데 필요한 기본 권한은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-114">The basic permissions required to run the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="920c4-115">MDS 구성 관리자와 동일한 Windows 권한(Windows 관리자)</span><span class="sxs-lookup"><span data-stu-id="920c4-115">The same Windows permission as the MDS Configuration Manager (administrator of Windows)</span></span>  
  
    -   <span data-ttu-id="920c4-116">MDS 데이터베이스에 대한 DBA 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-116">DBA permission on the MDS database.</span></span>  
  
2.  <span data-ttu-id="920c4-117">MDSModelDeploy 도구를 사용하여 패키지를 만드는 데 필요한 권한은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-117">The permissions required to create the package using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="920c4-118">데이터 모델에 대한 MDS 모델 관리자 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-118">MDS model administrator permission on the data model.</span></span>  
  
    -   <span data-ttu-id="920c4-119">MDS 통합 관리 기능 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-119">MDS Integration Management function permission.</span></span>  
  
3.  <span data-ttu-id="920c4-120">MDSModelDeploy 도구를 사용하여 모델을 배포하는 데 필요한 권한은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-120">The permissions required to deploy a model using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="920c4-121">MDS 탐색기 함수 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-121">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="920c4-122">MDS 통합 관리 기능 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-122">MDS Integration Management function permission</span></span>  
  
    -   <span data-ttu-id="920c4-123">MDS 시스템 관리 기능 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-123">MDS System Administration function permission.</span></span>  
  
4.  <span data-ttu-id="920c4-124">MDSModelDeploy 도구를 사용하여 모델을 나열하는 데 필요한 권한은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-124">The permissions required to list models using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="920c4-125">MDS 탐색기 함수 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-125">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="920c4-126">목록의 모델을 보기 위한 데이터 모델에 대한 MDS 모델 관리자 권한</span><span class="sxs-lookup"><span data-stu-id="920c4-126">MDS model administrator permission on the data model on order to see the model in the list.</span></span>  
  
 <span data-ttu-id="920c4-127">패키지를 만들 모델이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-127">A model must exist for you to create a package of.</span></span> <span data-ttu-id="920c4-128">자세한 내용은 [모델 만들기&#40;Master Data Services&#41;](create-a-model-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="920c4-128">For more information, see [Create a Model &#40;Master Data Services&#41;](create-a-model-master-data-services.md).</span></span>  
  
 <span data-ttu-id="920c4-129">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="920c4-129">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="920c4-130">MDSModelDeploy를 사용하여 모델 배포 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="920c4-130">To create a model deployment package by using MDSModelDeploy</span></span>  
  
1.  <span data-ttu-id="920c4-131">명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-131">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="920c4-132">MDSModelDeploy.exe의 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-132">Navigate to the location of MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="920c4-133">MDS를 기본 위치에 설치한 경우 파일은 *드라이브*: Files\Microsoft SQL Server\120\Master Data services\configuration에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-133">If MDS was installed in the default location, the file is in *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
    -   <span data-ttu-id="920c4-134">MDS를 기본 위치에 설치하지 않은 경우 로컬 컴퓨터에서 MDSModelDeploy.exe를 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="920c4-134">If MDS was not installed in the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="920c4-135">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-135">Optional.</span></span> <span data-ttu-id="920c4-136">보기 옵션 및 도움말입니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-136">View options and help.</span></span>  
  
    -   <span data-ttu-id="920c4-137">모든 사용 가능한 옵션을 표시하려면 `MDSModelDeploy` 를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-137">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="920c4-138">옵션에 대한 도움말을 표시하려면 *과 같이 입력합니다. 여기서* OptionName `MDSModelDeploy help OptionName`은 옵션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-138">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="920c4-139">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-139">Optional.</span></span> <span data-ttu-id="920c4-140">여러 웹 애플리케이션이 있는 경우 이 명령을 입력하고 Enter 키를 눌러 배포할 서비스의 이름을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-140">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="920c4-141">값의 목록(예: `MDS1, Default Web Site, MDS`)이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-141">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="920c4-142">이 목록의 첫 번째 값(이 경우 `MDS1`)은 모델을 배포하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-142">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="920c4-143">모델 개체와 데이터를 포함하는 패키지를 만들려면 다음과 같이 입력하십시오. 여기서 *ModelName*, *VersionName*, *ServiceName*및 *PackageName* 은 각각 모델, 버전, 서비스 및 .pkg 출력 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-143">To create a package that contains model objects and data, type the following, where *ModelName*, *VersionName*, *ServiceName*,  and *PackageName* are the names of the model, version, service, and of the .pkg output file respectively:</span></span>  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     <span data-ttu-id="920c4-144">데이터를 포함하지 않으려면 `-version` 및 `-includedata` 스위치를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="920c4-144">If you do not want to include data, do not use the `-version` and `-includedata` switches.</span></span>  
  
6.  <span data-ttu-id="920c4-145">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-145">Press Enter.</span></span> <span data-ttu-id="920c4-146">패키지가 성공적으로 만들어지면 "MDSModelDeploy 작업이 성공적으로 완료되었습니다."라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="920c4-146">When the package is successfully created, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="920c4-147">다음 단계</span><span class="sxs-lookup"><span data-stu-id="920c4-147">Next Steps</span></span>  
  
-   [<span data-ttu-id="920c4-148">MDSModelDeploy를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="920c4-148">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a><span data-ttu-id="920c4-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="920c4-149">See Also</span></span>  
 <span data-ttu-id="920c4-150">[모델 배포 옵션 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="920c4-150">[Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span></span>  
 [<span data-ttu-id="920c4-151">모델 배포&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="920c4-151">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
