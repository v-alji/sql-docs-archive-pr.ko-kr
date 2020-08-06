---
title: 일반 (데이터베이스 복원 대화 상자) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25a49e17227fc2ed6b7b18d2e0964cd8812cbdcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660748"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="a2baa-102">일반(데이터베이스 복원 대화 상자)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="a2baa-102">General (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a2baa-103">**에서** 데이터베이스 복원 **대화 상자의** 일반 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 복원할 때 사용할 백업 파일 및 일반 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-103">Use the **General** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the backup file and general settings to use when restoring an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2baa-104">복원 명령을 실행하는 사용자는 각 백업 파일에 대해 지정한 백업 위치에서 읽을 수 있는 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="a2baa-105">서버에 설치되지 않은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 복원하려면 사용자도 해당 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="a2baa-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 덮어쓰려면 사용자가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버이거나 복원할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2baa-107">기존 데이터베이스를 복원한 다음에는 해당 데이터베이스를 복원한 사용자가 보유하고 있는 복원된 데이터베이스 액세스 권한이 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="a2baa-108">이러한 액세스 권한 손실은 백업 수행 당시에 사용자가 서버 역할의 멤버가 아니었거나 모든 권한(관리자)이 있는 데이터베이스 역할의 멤버가 아니었던 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="a2baa-109">**데이터베이스 복원 대화 상자에서 일반 페이지를 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="a2baa-109">**To display the General page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="a2baa-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 **인스턴스의** 데이터베이스 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 폴더 또는 **개체 탐색기**의 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **복원**을 클릭한 다음 **페이지 선택**에서 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **General**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a2baa-111">옵션</span><span class="sxs-lookup"><span data-stu-id="a2baa-111">Options</span></span>  
 <span data-ttu-id="a2baa-112">**스크립트**</span><span class="sxs-lookup"><span data-stu-id="a2baa-112">**Script**</span></span>  
 <span data-ttu-id="a2baa-113">대화 상자에서 선택한 옵션을 기반으로 하는 복원 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="a2baa-114">복원 스크립트는 ASSL( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language)로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="a2baa-115">**스크립트** 아이콘을 클릭하면 기본적으로 복원 스크립트가 새 쿼리 창으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="a2baa-116">**스크립트** 화살표를 클릭하면 복원 스크립트를 보낼 위치를 선택할 수 있는 메뉴가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="a2baa-117">새 쿼리 창으로(기본값)</span><span class="sxs-lookup"><span data-stu-id="a2baa-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="a2baa-118">파일로</span><span class="sxs-lookup"><span data-stu-id="a2baa-118">To a file.</span></span>  
  
-   <span data-ttu-id="a2baa-119">클립보드로</span><span class="sxs-lookup"><span data-stu-id="a2baa-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="a2baa-120">작업으로</span><span class="sxs-lookup"><span data-stu-id="a2baa-120">To a job.</span></span>  
  
 <span data-ttu-id="a2baa-121">**데이터베이스 복원**</span><span class="sxs-lookup"><span data-stu-id="a2baa-121">**Restore database**</span></span>  
 <span data-ttu-id="a2baa-122">복원할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-122">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to restore.</span></span>  
  
 <span data-ttu-id="a2baa-123">**원본 백업 파일**</span><span class="sxs-lookup"><span data-stu-id="a2baa-123">**From backup file**</span></span>  
 <span data-ttu-id="a2baa-124">선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 복원할 백업 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-124">Select the backup file from which to restore the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="a2baa-125">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="a2baa-125">**Browse**</span></span>  
 <span data-ttu-id="a2baa-126">**데이터베이스 파일 찾기** 대화 상자를 표시하고 사용할 백업 파일의 경로 및 파일 이름을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-126">Click to display the **Locate Database Files** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="a2baa-127">**데이터베이스 파일 찾기** 대화 상자에 대한 자세한 내용은 [데이터베이스 파일 찾기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2baa-127">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="a2baa-128">**데이터베이스 덮어쓰기 허용**</span><span class="sxs-lookup"><span data-stu-id="a2baa-128">**Allow database overwrite**</span></span>  
 <span data-ttu-id="a2baa-129">선택한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 모든 기존 개체에 대해 선택한 백업 파일의 내용을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 복원할 수 있게 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-129">Select to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to restore the contents of the selected backup file over any existing objects in the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="a2baa-130">**보안 정보 포함**</span><span class="sxs-lookup"><span data-stu-id="a2baa-130">**Include security information**</span></span>  
 <span data-ttu-id="a2baa-131">백업 파일에 저장된 보안 정보를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스로 복사하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-131">Select to copy any security information stored in the backup file to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="a2baa-132">이 옵션을 선택하면 사용 가능한 드롭다운 목록에서 보안 정보의 양을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-132">If this option is selected, you can choose the amount of security information from the drop-down list enabled by selecting this option.</span></span> <span data-ttu-id="a2baa-133">다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-133">The following options are available:</span></span>  
  
|<span data-ttu-id="a2baa-134">옵션</span><span class="sxs-lookup"><span data-stu-id="a2baa-134">Option</span></span>|<span data-ttu-id="a2baa-135">Description</span><span class="sxs-lookup"><span data-stu-id="a2baa-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a2baa-136">**모두 복사**</span><span class="sxs-lookup"><span data-stu-id="a2baa-136">**Copy All**</span></span>|<span data-ttu-id="a2baa-137">백업 파일에 포함된 데이터베이스 역할 및 해당 역할과 연결된 사용자 계정을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-137">Restores the database roles contained in the backup file, as well as the user accounts associated with the roles.</span></span>|  
|<span data-ttu-id="a2baa-138">**멤버 등록 건너뛰기**</span><span class="sxs-lookup"><span data-stu-id="a2baa-138">**Skip Membership**</span></span>|<span data-ttu-id="a2baa-139">백업 파일에 포함된 데이터베이스 역할만 복원하고 해당 역할과 연결된 사용자 계정은 복원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-139">Restores the database roles contained in the backup file, but does not restore the user accounts associated with the roles.</span></span>|  
  
 <span data-ttu-id="a2baa-140">**암호**</span><span class="sxs-lookup"><span data-stu-id="a2baa-140">**Password**</span></span>  
 <span data-ttu-id="a2baa-141">백업 파일이 암호화된 경우 백업 파일을 암호화하는 데 사용한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a2baa-141">If the backup file is encrypted, type the password used to encrypt the backup file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2baa-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2baa-142">See Also</span></span>  
 <span data-ttu-id="a2baa-143">[데이터베이스 복원 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a2baa-143">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a2baa-144">[파티션 &#40;데이터베이스 복원 대화 상자&#41; &#40;Analysis Services-다차원 데이터&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a2baa-144">[Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a2baa-145">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="a2baa-145">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
