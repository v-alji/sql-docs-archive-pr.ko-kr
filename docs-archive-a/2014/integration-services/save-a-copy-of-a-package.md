---
title: 패키지 복사본 저장 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 02ee2374fddb7dbb6b17adc2a4a10707179c882d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730832"
---
# <a name="save-a-copy-of-a-package"></a><span data-ttu-id="d6321-102">패키지의 복사본 저장</span><span class="sxs-lookup"><span data-stu-id="d6321-102">Save a Copy of a Package</span></span>
  <span data-ttu-id="d6321-103">이 절차에서는 파일 시스템, 패키지 저장소 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 **msdb** 데이터베이스에 패키지 복사본을 저장하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-103">This procedure describes how to save a copy of a package to the file system, to the package store, or to the **msdb** database in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d6321-104">패키지 복사본의 저장 위치를 지정할 때 패키지 이름을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-104">When you specify a location to save the package copy, you can also update the name of the package.</span></span>  
  
 <span data-ttu-id="d6321-105">패키지 저장소에는 **msdb** 데이터베이스와 파일 시스템의 폴더가 모두 포함될 수도 있고, **msdb**또는 파일 시스템의 폴더 중 하나만 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-105">The package store can include both the **msdb** database and the folders in the file system, only **msdb**, or only folders in the file system.</span></span> <span data-ttu-id="d6321-106">**msdb**에서 패키지는 **sysssispackages** 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-106">In **msdb**, packages are saved to the **sysssispackages** table.</span></span> <span data-ttu-id="d6321-107">이 테이블에는 패키지가 속한 논리적 폴더를 식별하는 **folderid** 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-107">This table includes a **folderid** column that identifies the logical folder to which the package belongs.</span></span> <span data-ttu-id="d6321-108">논리적 폴더를 사용하면 파일 시스템의 폴더를 통해 파일 시스템에 저장된 패키지를 그룹화할 수 있는 것과 동일한 방식으로 **msdb** 에 저장된 패키지를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-108">The logical folders provide a useful way to group packages saved to **msdb** in the same way that folders in the file system provide a way to group packages saved to the file system.</span></span> <span data-ttu-id="d6321-109">**msdb** 의 **sysssispackagefolders** 테이블에 있는 행은 폴더를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-109">Rows in the **sysssispackagefolders** table in **msdb** define the folders.</span></span>  
  
 <span data-ttu-id="d6321-110">**msdb** 가 패키지 저장소의 일부로 정의되어 있지 않은 경우 **패키지 경로** 옵션에서 SQL Server를 선택할 때 패키지를 기존 논리적 폴더와 계속 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-110">If **msdb** is not defined as part of the package store, you can continue to associate packages with existing logical folders when you select SQL Server in the **Package Path** option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6321-111">패키지 복사본을 저장하려면 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 패키지를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-111">The package must be opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer before you can save a copy of the package.</span></span>  
  
### <a name="to-save-a-copy-of-a-package"></a><span data-ttu-id="d6321-112">패키지 복사본을 저장하려면</span><span class="sxs-lookup"><span data-stu-id="d6321-112">To save a copy of a package</span></span>  
  
1.  <span data-ttu-id="d6321-113">솔루션 탐색기에서 복사본을 저장하려는 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-113">In Solution Explorer, double-click the package of which you want to save a copy.</span></span>  
  
2.  <span data-ttu-id="d6321-114">**파일** 메뉴에서 **다른 이름으로 \<package file>의 복사본 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-114">On the **File** menu, click **Save Copy of \<package file> As**.</span></span>  
  
3.  <span data-ttu-id="d6321-115">**패키지 복사본 저장** 대화 상자의 **패키지 위치** 목록에서 패키지 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-115">In the **Save Copy of Package** dialog box, select a package location in the **Package location** list.</span></span>  
  
4.  <span data-ttu-id="d6321-116">위치가 **SQL Server** 또는 **SSIS 패키지 저장소**인 경우 서버 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-116">If the location is **SQL Server** or **SSIS Package Store**, provide a server name.</span></span>  
  
5.  <span data-ttu-id="d6321-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]로 저장하는 경우에는 인증 유형을 지정하고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우에는 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-117">If saving to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify the authentication type and, if using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and password.</span></span>  
  
6.  <span data-ttu-id="d6321-118">패키지 경로를 지정하려면 해당 경로를 직접 입력하거나, 찾아보기 단추 **(…)** 를 클릭하고 패키지 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-118">To specify the package path, either type the path or click the browse button **(...)** to specify the location of the package.</span></span> <span data-ttu-id="d6321-119">패키지의 기본 이름은 Package입니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-119">The default name of the package is Package.</span></span> <span data-ttu-id="d6321-120">필요에 맞게 패키지 이름을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-120">Optionally, update the package name to one that suits your needs.</span></span>  
  
     <span data-ttu-id="d6321-121">**패키지 경로** 옵션으로 **SQL Server** 를 선택하면 패키지 경로는 **msdb** 의 논리적 폴더와 패키지 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-121">If you select **SQL Server** as the **Package Path** option, the package path consists of logical folders in **msdb** and the package name.</span></span> <span data-ttu-id="d6321-122">예를 들어 DownloadMonthlyData 패키지가 MSDB 폴더( **msdb**에 있는 논리적 루트 폴더의 기본 이름) 내의 Finance 폴더와 연결되어 있으면 DownloadMonthlyData 패키지의 패키지 경로는 MSDB/Finance/DownloadMonthlyData가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-122">For example, if the package DownloadMonthlyData is associated with the Finance folder within the MSDB folder (the default name of the root logical folder in **msdb**), the package path for the package named DownloadMonthlyData is MSDB/Finance/DownloadMonthlyData</span></span>  
  
     <span data-ttu-id="d6321-123">**패키지 경로** 옵션으로 **SSIS 패키지 저장소** 를 선택하면 패키지 경로는 Integration Services 서비스에서 관리하는 폴더로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-123">If you select **SSIS Package Store** as the **Package Path** option, the package path consists of the folder that the Integration Services service manages.</span></span> <span data-ttu-id="d6321-124">예를 들어 UpdateDeductions 패키지가 Integration Services 서비스에서 관리하는 파일 시스템 폴더 내의 HumanResources 폴더에 있으면 해당 패키지 경로는 /File System/HumanResources/UpdateDeductions가 됩니다. 마찬가지로 PostResumes 패키지가 MSDB 폴더 내의 HumanResources 폴더와 연결되어 있으면 해당 패키지 경로는 MSDB/HumanResources/PostResumes가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-124">For example, if the package UpdateDeductions is located in the HumanResources folder within the file system folder that the service manages, the package path is /File System/HumanResources/UpdateDeductions; likewise, if the package PostResumes is associated with the HumanResources folder within the MSDB folder, the package path is MSDB/HumanResources/PostResumes.</span></span>  
  
     <span data-ttu-id="d6321-125">**패키지 경로** 옵션으로 **파일 시스템** 을 선택하면 패키지 경로는 파일 시스템에서의 위치와 파일 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-125">If you select **File System** as the **Package Path** option, the package path is the location in the file system and the file name.</span></span> <span data-ttu-id="d6321-126">예를 들어 패키지 이름이 UpdateDemographics이면 패키지 경로는 C:\HumanResources\Quarterly\UpdateDemographics.dtsx와 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-126">For example, if the package name is UpdateDemographics the package path is C:\HumanResources\Quarterly\UpdateDemographics.dtsx.</span></span>  
  
7.  <span data-ttu-id="d6321-127">패키지 보호 수준을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-127">Review the package protection level.</span></span>  
  
8.  <span data-ttu-id="d6321-128">선택적으로 **보호 수준** 상자 옆에 있는 찾아보기 단추 **(…)** 를 클릭하여 보호 수준을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-128">Optionally, click the browse button **(...)** by the **Protection level** box to change the protection level.</span></span>  
  
    -   <span data-ttu-id="d6321-129">**패키지 보호 수준** 대화 상자에서 다른 보호 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-129">In the **Package Protection Level** dialog box, select a different protection level.</span></span>  
  
    -   <span data-ttu-id="d6321-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-130">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d6321-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6321-131">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6321-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6321-132">See Also</span></span>  
 <span data-ttu-id="d6321-133">[SSIS&#41; 패키지 Integration Services &#40;](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="d6321-133">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="d6321-134">Integration Services 서비스 구성&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="d6321-134">Configuring the Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  
