---
title: 데이터베이스 백업 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Backup.f1
ms.assetid: 7811ce7d-6c37-4189-bfa6-ef36fb4932db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 48cf094353c53213864dae656af94ae791442105
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648155"
---
# <a name="backup-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6aedc-102">데이터베이스 백업 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="6aedc-102">Backup Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6aedc-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 **데이터베이스 백업** 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 백업 파일(.abf) 형식을 사용하는 백업 파일에 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-103">Use the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to back up an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6aedc-104">백업 명령을 실행하는 사용자에게는 각 백업 파일에 대해 지정한 백업 위치에 쓸 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-104">For each backup file, the user who runs the backup command must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="6aedc-105">또한 사용자는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버이거나 백업할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-105">Also, the user must have one of the following roles: a member of a server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
 <span data-ttu-id="6aedc-106">**데이터베이스 백업 대화 상자를 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="6aedc-106">**To display the Backup Database dialog box**</span></span>  
  
-   <span data-ttu-id="6aedc-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 **데이터베이스** 폴더 또는 **개체 탐색기**의 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-107">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Backup**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6aedc-108">옵션</span><span class="sxs-lookup"><span data-stu-id="6aedc-108">Options</span></span>  
 <span data-ttu-id="6aedc-109">**스크립트**</span><span class="sxs-lookup"><span data-stu-id="6aedc-109">**Script**</span></span>  
 <span data-ttu-id="6aedc-110">대화 상자에서 선택한 옵션을 기반으로 하는 백업 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-110">Creates a backup script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="6aedc-111">복원 스크립트는 ASSL( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language)로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-111">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="6aedc-112">**스크립트** 아이콘을 클릭하면 기본적으로 백업 스크립트가 새 쿼리 창으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-112">Clicking the **Script** icon sends the backup script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="6aedc-113">**스크립트** 화살표를 클릭하면 백업 스크립트를 보낼 위치를 선택할 수 있는 메뉴가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-113">Clicking the **Script** arrow displays a menu that allows you to choose where to send the backup script:</span></span>  
  
-   <span data-ttu-id="6aedc-114">새 쿼리 창으로(기본값)</span><span class="sxs-lookup"><span data-stu-id="6aedc-114">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="6aedc-115">파일로</span><span class="sxs-lookup"><span data-stu-id="6aedc-115">To a file.</span></span>  
  
-   <span data-ttu-id="6aedc-116">클립보드로</span><span class="sxs-lookup"><span data-stu-id="6aedc-116">To the clipboard.</span></span>  
  
-   <span data-ttu-id="6aedc-117">작업으로</span><span class="sxs-lookup"><span data-stu-id="6aedc-117">To a job.</span></span>  
  
 <span data-ttu-id="6aedc-118">**Database**</span><span class="sxs-lookup"><span data-stu-id="6aedc-118">**Database**</span></span>  
 <span data-ttu-id="6aedc-119">현재 선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-119">Displays the name of the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="6aedc-120">**백업 파일**</span><span class="sxs-lookup"><span data-stu-id="6aedc-120">**Backup file**</span></span>  
 <span data-ttu-id="6aedc-121">사용할 백업 파일의 전체 경로 및 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-121">Type the full path and file name of the backup file to use.</span></span>  
  
 <span data-ttu-id="6aedc-122">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="6aedc-122">**Browse**</span></span>  
 <span data-ttu-id="6aedc-123">**다른 이름으로 파일 저장** 대화 상자를 표시하고 사용할 백업 파일의 경로 및 파일 이름을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-123">Click to display the **Save File As** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="6aedc-124">**다른 이름으로 파일 저장** 대화 상자에 대한 자세한 내용은 [다른 이름으로 파일 저장 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6aedc-124">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="6aedc-125">**파일 덮어쓰기 허용**</span><span class="sxs-lookup"><span data-stu-id="6aedc-125">**Allow file overwrite**</span></span>  
 <span data-ttu-id="6aedc-126">기존 백업 파일 또는 원격 백업 파일이 있는 경우 덮어쓰려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-126">Select to overwrite an existing backup file or remote backup file, if one exists.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aedc-127">이 옵션을 선택하지 않은 경우 **백업 파일**에서 지정한 백업 파일 또는 **원격 백업 파일**에서 지정한 원격 백업 파일이 존재하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-127">If this option is not selected and the backup file specified in **Backup file** or a remote backup file specified in **Remote backup file** exists, an error occurs.</span></span>  
  
 <span data-ttu-id="6aedc-128">**압축 적용**</span><span class="sxs-lookup"><span data-stu-id="6aedc-128">**Apply compression**</span></span>  
 <span data-ttu-id="6aedc-129">백업 파일 및 원격 백업 파일(지정한 경우)의 내용을 압축하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-129">Select to compress the contents of the backup file and, if specified, remote backup files.</span></span>  
  
 <span data-ttu-id="6aedc-130">**백업 파일 암호화**</span><span class="sxs-lookup"><span data-stu-id="6aedc-130">**Encrypt backup file**</span></span>  
 <span data-ttu-id="6aedc-131">**암호**에 입력한 암호를 사용하여 백업 파일을 암호화하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-131">Select to encrypt the backup file using the password supplied in **Password**.</span></span>  
  
 <span data-ttu-id="6aedc-132">**암호**</span><span class="sxs-lookup"><span data-stu-id="6aedc-132">**Password**</span></span>  
 <span data-ttu-id="6aedc-133">백업 파일 및 원격 백업 파일(지정한 경우)을 암호화하는 데 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-133">Type the password to use when encrypting the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aedc-134"> 이 옵션은 **백업 파일 암호화** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-134">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="6aedc-135">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="6aedc-135">**Confirm Password**</span></span>  
 <span data-ttu-id="6aedc-136">백업 파일 및 원격 백업 파일(지정된 경우)의 암호를 확인하려면 **암호** 에 입력한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-136">Type the password entered in **Password** to confirm the password for the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aedc-137"> 이 옵션은 **백업 파일 암호화** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-137">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="6aedc-138">**원격 파티션 백업**</span><span class="sxs-lookup"><span data-stu-id="6aedc-138">**Backup remote partition(s)**</span></span>  
 <span data-ttu-id="6aedc-139">백업 파일에 원격 파티션에 대한 위치 정보 및 데이터를 포함하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-139">Select to include location information and data for remote partitions in the backup file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aedc-140">이 옵션은 현재 선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스가 원격 파티션을 사용하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-140">This option is enabled only if the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database uses remote partitions.</span></span>  
  
 <span data-ttu-id="6aedc-141">**원격 파티션 백업 위치**</span><span class="sxs-lookup"><span data-stu-id="6aedc-141">**Remote partition backup location**</span></span>  
 <span data-ttu-id="6aedc-142">원격 파티션에 대한 데이터 및 메타데이터를 백업하는 데 사용된 원격 백업 파일을 비롯하여 선택한 데이터베이스와 연결된 원격 파티션의 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-142">Displays the location of remote partitions associated with the selected database, as well as the remote backup file used to back up the data and metadata for the remote partitions.</span></span> <span data-ttu-id="6aedc-143">사용할 수 있는 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-143">The following columns are available:</span></span>  
  
|<span data-ttu-id="6aedc-144">열</span><span class="sxs-lookup"><span data-stu-id="6aedc-144">Column</span></span>|<span data-ttu-id="6aedc-145">Description</span><span class="sxs-lookup"><span data-stu-id="6aedc-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6aedc-146">**Server**</span><span class="sxs-lookup"><span data-stu-id="6aedc-146">**Server**</span></span>|<span data-ttu-id="6aedc-147">원격 파티션을 관리하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-147">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partitions.</span></span>|  
|<span data-ttu-id="6aedc-148">**Database**</span><span class="sxs-lookup"><span data-stu-id="6aedc-148">**Database**</span></span>|<span data-ttu-id="6aedc-149">원격 파티션을 포함하는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-149">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that contains the remote partitions.</span></span>|  
|<span data-ttu-id="6aedc-150">**파티션 목록**</span><span class="sxs-lookup"><span data-stu-id="6aedc-150">**Partition List**</span></span>|<span data-ttu-id="6aedc-151">**데이터베이스**에 표시된 데이터베이스가 포함하는 원격 파티션의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-151">Displays the list of remote partitions contained by the database displayed in **Database**.</span></span>|  
|<span data-ttu-id="6aedc-152">**원격 백업 파일**</span><span class="sxs-lookup"><span data-stu-id="6aedc-152">**Remote backup file**</span></span>|<span data-ttu-id="6aedc-153">사용할 원격 백업 파일의 전체 경로 및 파일 이름을 입력하거나 줄임표 단추(**...**)를 클릭하여 **다른 이름으로 파일 저장** 대화 상자를 표시하고 사용할 원격 백업 파일의 경로 및 파일 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6aedc-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Save File As** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="6aedc-154">**다른 이름으로 파일 저장** 대화 상자에 대한 자세한 내용은 [다른 이름으로 파일 저장 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6aedc-154">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6aedc-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6aedc-155">See Also</span></span>  
 <span data-ttu-id="6aedc-156">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6aedc-156">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="6aedc-157">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="6aedc-157">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
