---
title: 데이터베이스 복원 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
ms.openlocfilehash: f45a41eb10e81e1cfe1100045cc4d00353cb11fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743527"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="5fc11-102">데이터베이스 복원 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="5fc11-102">Restore Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5fc11-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 **데이터베이스 복원** 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 백업 파일(.abf) 형식을 사용하는 백업 파일에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-103">Use the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database from a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5fc11-104">복원 명령을 실행하는 사용자는 각 백업 파일에 대해 지정한 백업 위치에서 읽을 수 있는 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="5fc11-105">서버에 설치되지 않은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 복원하려면 사용자도 해당 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="5fc11-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 덮어쓰려면 사용자가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버이거나 복원할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fc11-107">기존 데이터베이스를 복원한 다음에는 해당 데이터베이스를 복원한 사용자가 보유하고 있는 복원된 데이터베이스 액세스 권한이 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="5fc11-108">이러한 액세스 권한 손실은 백업 수행 당시에 사용자가 서버 역할의 멤버가 아니었거나 모든 권한(관리자)이 있는 데이터베이스 역할의 멤버가 아니었던 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="5fc11-109">**데이터베이스 복원 대화 상자를 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="5fc11-109">**To display the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="5fc11-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 **인스턴스의** 데이터베이스 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 폴더 또는 **개체 탐색기**의 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Restore**.</span></span>  
  
 <span data-ttu-id="5fc11-111">**데이터베이스 복원** 대화 상자에는 다음 페이지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-111">The **Restore Database** dialog box contains the following pages.</span></span>  
  
## <a name="pages"></a><span data-ttu-id="5fc11-112">페이지</span><span class="sxs-lookup"><span data-stu-id="5fc11-112">Pages</span></span>  
 <span data-ttu-id="5fc11-113">**일반**</span><span class="sxs-lookup"><span data-stu-id="5fc11-113">**General**</span></span>  
 <span data-ttu-id="5fc11-114">이 페이지를 사용하여 데이터베이스 복원 중에 사용할 일반 옵션 및 암호를 비롯하여 복원할 데이터베이스, 데이터베이스를 복원할 백업 파일을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-114">Use this page to select the database to restore, the backup file from which to restore the database, as well as the general options and password to use while restoring the database.</span></span> <span data-ttu-id="5fc11-115">이 페이지에 대한 자세한 내용은 [일반&#40;데이터베이스 복원 대화 상자&#41;&#40;Analysis Services - 다차원 데이터&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fc11-115">For more information about this page, see [General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5fc11-116">**파티션**</span><span class="sxs-lookup"><span data-stu-id="5fc11-116">**Partitions**</span></span>  
 <span data-ttu-id="5fc11-117">이 페이지를 사용하여 지정한 위치에 로컬 파티션을 복원하고, 원격 백업 파일에서 원격 파티션을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc11-117">Use this page to restore local partitions to specified locations, and to restore remote partitions from remote backup files.</span></span> <span data-ttu-id="5fc11-118">이 페이지에 대한 자세한 내용은 [파티션&#40;데이터베이스 복원 대화 상자&#41;&#40;Analysis Services - 다차원 데이터&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fc11-118">For more information about this page, see [Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc11-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fc11-119">See Also</span></span>  
 <span data-ttu-id="5fc11-120">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5fc11-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5fc11-121">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="5fc11-121">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
