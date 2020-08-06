---
title: 복원 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3fa8da816e656521fb04ae7beb1127786e04e178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743552"
---
# <a name="restore-options"></a><span data-ttu-id="e5deb-102">복원 옵션</span><span class="sxs-lookup"><span data-stu-id="e5deb-102">Restore Options</span></span>
  <span data-ttu-id="e5deb-103">여러 가지 방법으로 데이터베이스를 복원할 수 있습니다 .이 경우에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 모두 서버 컴퓨터와 데이터베이스에 대 한 관리자 권한이 있어야 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-103">There are many ways to restore your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, all of which require that you have administrator permissions for both the server computer and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="e5deb-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 복원할 경우 **에서** 데이터베이스 복원 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]대화 상자를 열고 적합한 옵션 구성을 선택한 다음 대화 상자에서 복원을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-104">To restore an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, you can open the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the appropriate options configuration and then run the restore from the dialog box.</span></span> <span data-ttu-id="e5deb-105">또는 파일에 이미 지정된 설정을 사용하는 스크립트를 만들어 저장하고 필요할 때마다 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-105">Or, you can create a script using the settings already specified in the file; the script can then be saved and run as often as needed.</span></span> <span data-ttu-id="e5deb-106">이 방식으로 다음 섹션에 설명된 것과 같이 XMLA를 사용하여 복원을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-106">In this way, the restore is completed by using XMLA, as described in the next section.</span></span>  
  
## <a name="restoring-databases-using-xmla"></a><span data-ttu-id="e5deb-107">XMLA를 사용하여 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="e5deb-107">Restoring Databases Using XMLA</span></span>  
 <span data-ttu-id="e5deb-108">XMLA 복원 명령은 .abf 파일을 기반으로 복원을 실행하여 복원 프로세스를 자동화하기 위한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-108">The XMLA Restore command is a way to automate the restore process by running a restore based on an .abf file.</span></span> <span data-ttu-id="e5deb-109">복원 명령에는 보안 정의, 원격 파티션을 저장할 위치 및 관계형 OLAP(ROLAP) 개체의 재할당을 지정하도록 설정할 수 있는 여러 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-109">The Restore command has a number of properties that can be set to specify security definitions, where remote partitions should be stored, and the relocation of relational OLAP (ROLAP) objects.</span></span> <span data-ttu-id="e5deb-110">자세한 내용은 [Restore 요소&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5deb-110">For more information, see [Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e5deb-111">복원 명령을 실행하는 사용자는 각 백업 파일에 대해 지정한 백업 위치에서 읽을 수 있는 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-111">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="e5deb-112">서버에 설치되지 않은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 복원하려면 사용자도 해당 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-112">To restore an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="e5deb-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 덮어쓰려면 사용자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 서버 역할의 멤버이거나 복원할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-113">To overwrite an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5deb-114">기존 데이터베이스를 복원한 다음에는 해당 데이터베이스를 복원한 사용자가 보유하고 있는 복원된 데이터베이스 액세스 권한이 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-114">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="e5deb-115">이러한 액세스 권한 손실은 백업 수행 당시에 사용자가 서버 역할의 멤버가 아니었거나 모든 권한(관리자)이 있는 데이터베이스 역할의 멤버가 아니었던 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5deb-115">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5deb-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5deb-116">See Also</span></span>  
 <span data-ttu-id="e5deb-117">[데이터베이스 복원 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e5deb-117">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="e5deb-118">[Analysis Services 데이터베이스 백업 및 복원](backup-and-restore-of-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e5deb-118">[Backup and Restore of Analysis Services Databases](backup-and-restore-of-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="e5deb-119">[Restore 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="e5deb-119">[Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) </span></span>  
 [<span data-ttu-id="e5deb-120">데이터베이스 백업, 복원 및 동기화&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="e5deb-120">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
