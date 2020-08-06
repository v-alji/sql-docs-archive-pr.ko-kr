---
title: 파티션 (데이터베이스 복원 대화 상자) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
ms.openlocfilehash: b54ac204cd09651a933f1c53c7780fc96ae1bfb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659691"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="20fc9-102">파티션(데이터베이스 복원 대화 상자)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="20fc9-102">Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="20fc9-103">\*\*\*\* 데이터베이스 복원 **대화 상자의** 파티션 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 페이지를 사용하여 로컬 파티션을 복원할 위치를 지정하고 원격 파티션 복원 여부와 원격 파티션 복원 시 사용할 원격 백업 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-103">Use the **Partitions** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the location to restore local partitions, and to specify whether to restore remote partitions and the remote backup files to use when restoring remote partitions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20fc9-104">복원 명령을 실행하는 사용자는 각 백업 파일에 대해 지정한 백업 위치에서 읽을 수 있는 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="20fc9-105">서버에 설치되지 않은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 복원하려면 사용자도 해당 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="20fc9-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 덮어쓰려면 사용자가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버이거나 복원할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20fc9-107">기존 데이터베이스를 복원한 다음에는 해당 데이터베이스를 복원한 사용자가 보유하고 있는 복원된 데이터베이스 액세스 권한이 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="20fc9-108">이러한 액세스 권한 손실은 백업 수행 당시에 사용자가 서버 역할의 멤버가 아니었거나 모든 권한(관리자)이 있는 데이터베이스 역할의 멤버가 아니었던 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="20fc9-109">**데이터베이스 복원 대화 상자에서 파티션 페이지를 표시 하려면**</span><span class="sxs-lookup"><span data-stu-id="20fc9-109">**To display the Partitions page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="20fc9-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 **인스턴스의** 데이터베이스 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 폴더 또는 **개체 탐색기**의 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **복원**을 클릭한 다음 **페이지 선택**에서 **파티션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **Partitions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="20fc9-111">옵션</span><span class="sxs-lookup"><span data-stu-id="20fc9-111">Options</span></span>  
 <span data-ttu-id="20fc9-112">**스크립트**</span><span class="sxs-lookup"><span data-stu-id="20fc9-112">**Script**</span></span>  
 <span data-ttu-id="20fc9-113">대화 상자에서 선택한 옵션을 기반으로 하는 복원 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="20fc9-114">복원 스크립트는 ASSL( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language)로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="20fc9-115">**스크립트** 아이콘을 클릭하면 기본적으로 복원 스크립트가 새 쿼리 창으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="20fc9-116">**스크립트** 화살표를 클릭하면 복원 스크립트를 보낼 위치를 선택할 수 있는 메뉴가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="20fc9-117">새 쿼리 창으로(기본값)</span><span class="sxs-lookup"><span data-stu-id="20fc9-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="20fc9-118">파일로</span><span class="sxs-lookup"><span data-stu-id="20fc9-118">To a file.</span></span>  
  
-   <span data-ttu-id="20fc9-119">클립보드로</span><span class="sxs-lookup"><span data-stu-id="20fc9-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="20fc9-120">작업으로</span><span class="sxs-lookup"><span data-stu-id="20fc9-120">To a job.</span></span>  
  
 <span data-ttu-id="20fc9-121">**원래 위치로 복원**</span><span class="sxs-lookup"><span data-stu-id="20fc9-121">**Restore to original locations**</span></span>  
 <span data-ttu-id="20fc9-122">백업 파일에 포함된 로컬 파티션을 원래 위치로 복원하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-122">Select to restore local partitions contained in the backup file to their original locations.</span></span>  
  
 <span data-ttu-id="20fc9-123">**다른 위치 선택**</span><span class="sxs-lookup"><span data-stu-id="20fc9-123">**Select different locations**</span></span>  
 <span data-ttu-id="20fc9-124">로컬 파티션을 복원할 다른 위치를 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-124">Select to specify different locations in which to restore local partitions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20fc9-125">큐브의 로컬 파티션에 대해 기본 위치 이외의 다른 위치를 지정한 경우에만 해당 파티션의 복원 폴더를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-125">You can only change the restoration folder of a local partition if a location other than the default location was specified for that partition in the cube.</span></span>  
  
 <span data-ttu-id="20fc9-126">이 옵션을 선택하면 활성화되는 다음 표는 각 로컬 파티션에 대한 복원 폴더를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-126">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="20fc9-127">열</span><span class="sxs-lookup"><span data-stu-id="20fc9-127">Column</span></span>|<span data-ttu-id="20fc9-128">Description</span><span class="sxs-lookup"><span data-stu-id="20fc9-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="20fc9-129">**Cube**</span><span class="sxs-lookup"><span data-stu-id="20fc9-129">**Cube**</span></span>|<span data-ttu-id="20fc9-130">로컬 파티션이 포함된 큐브 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-130">Displays the name of the cube that contains the local partition.</span></span>|  
|<span data-ttu-id="20fc9-131">**MeasureGroup**</span><span class="sxs-lookup"><span data-stu-id="20fc9-131">**MeasureGroup**</span></span>|<span data-ttu-id="20fc9-132">로컬 파티션이 포함된 측정값 그룹 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-132">Displays the name of the measure group that contains the local partition.</span></span>|  
|<span data-ttu-id="20fc9-133">**파티션**</span><span class="sxs-lookup"><span data-stu-id="20fc9-133">**Partition**</span></span>|<span data-ttu-id="20fc9-134">로컬 파티션 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-134">Displays the name of the local partition.</span></span>|  
|<span data-ttu-id="20fc9-135">**크기(MB)**</span><span class="sxs-lookup"><span data-stu-id="20fc9-135">**Size (MB)**</span></span>|<span data-ttu-id="20fc9-136">로컬 파티션의 크기(MB)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-136">Displays the size, in megabytes, of the local partition.</span></span>|  
|<span data-ttu-id="20fc9-137">**원본 폴더**</span><span class="sxs-lookup"><span data-stu-id="20fc9-137">**Original Folder**</span></span>|<span data-ttu-id="20fc9-138">로컬 파티션이 저장된 원본 폴더 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-138">Displays the name of the original folder in which the local partition was stored.</span></span>|  
|<span data-ttu-id="20fc9-139">**복원 폴더**</span><span class="sxs-lookup"><span data-stu-id="20fc9-139">**Restoration Folder**</span></span>|<span data-ttu-id="20fc9-140">로컬 파티션의 복원 폴더 이름을 입력하거나 줄임표 단추(**...**)를 클릭하여 **원격 폴더 찾아보기** 대화 상자를 표시하고 사용할 폴더의 경로를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-140">Type the name of the restoration folder for the local partition, or click the ellipsis button (**...**) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use.</span></span> <span data-ttu-id="20fc9-141">**원격 폴더 찾아보기** 대화 상자에 대한 자세한 내용은 [원격 폴더 찾아보기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20fc9-141">For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
 <span data-ttu-id="20fc9-142">**원격 파티션 복원**</span><span class="sxs-lookup"><span data-stu-id="20fc9-142">**Restore remote partitions**</span></span>  
 <span data-ttu-id="20fc9-143">원격 백업 파일에 저장된 원격 파티션을 복원하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-143">Select to restore remote partitions stored in remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20fc9-144">이 옵션은 원격 파티션에 대한 참조가 백업 파일에 포함된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-144">This option is enabled only if the backup file contains references to remote partitions.</span></span>  
  
 <span data-ttu-id="20fc9-145">이 옵션을 선택하면 활성화되는 다음 표는 각 로컬 파티션에 대한 복원 폴더를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-145">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="20fc9-146">열</span><span class="sxs-lookup"><span data-stu-id="20fc9-146">Column</span></span>|<span data-ttu-id="20fc9-147">Description</span><span class="sxs-lookup"><span data-stu-id="20fc9-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="20fc9-148">**Server**</span><span class="sxs-lookup"><span data-stu-id="20fc9-148">**Server**</span></span>|<span data-ttu-id="20fc9-149">원격 파티션을 관리하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-149">Displays the name of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partition.</span></span>|  
|<span data-ttu-id="20fc9-150">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="20fc9-150">**Data Source**</span></span>|<span data-ttu-id="20fc9-151">백업 파일에서 원격 파티션이 포함된 데이터베이스를 나타내는 데이터 원본 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-151">Displays the name of the data source in the backup file that represents the database that contains the remote partition.</span></span>|  
|<span data-ttu-id="20fc9-152">**백업 파일**</span><span class="sxs-lookup"><span data-stu-id="20fc9-152">**Backup File**</span></span>|<span data-ttu-id="20fc9-153">사용할 원격 백업 파일의 전체 경로 및 파일 이름을 입력하거나 줄임표 단추(**...**)를 클릭하여 **데이터베이스 파일 찾기** 대화 상자를 표시하고 사용할 원격 백업 파일의 경로 및 파일 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Locate Database Files** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="20fc9-154">**데이터베이스 파일 찾기** 대화 상자에 대한 자세한 내용은 [데이터베이스 파일 찾기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20fc9-154">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="20fc9-155">**...**</span><span class="sxs-lookup"><span data-stu-id="20fc9-155">**...**</span></span>|<span data-ttu-id="20fc9-156">**원격 파티션 - 고급 설정** 대화 상자를 표시하고 데이터 원본의 연결 문자열과 같은 원격 파티션 복원에 대한 고급 옵션을 수정하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20fc9-156">Click to display the **Remote Partitions - Advanced Settings** dialog box and modify advanced options, such as the connection string for the data source, for restoring the remote partition.</span></span> <span data-ttu-id="20fc9-157">**원격 파티션 - 고급 설정** 대화 상자에 대한 자세한 내용은 [원격 파티션 - 고급 설정 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20fc9-157">For more information about the **Remote Partitions - Advanced Settings** dialog box, see [Remote Partitions - Advanced Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20fc9-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20fc9-158">See Also</span></span>  
 <span data-ttu-id="20fc9-159">[데이터베이스 복원 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="20fc9-159">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="20fc9-160">[일반 &#40;데이터베이스 복원 대화 상자&#41; &#40;Analysis Services-다차원 데이터&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="20fc9-160">[General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="20fc9-161">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="20fc9-161">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
