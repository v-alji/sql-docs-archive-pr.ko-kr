---
title: 백업 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9fc674e699a3078ebd39d50fde96d632ae20493
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646700"
---
# <a name="backup-options"></a><span data-ttu-id="55413-102">백업 옵션</span><span class="sxs-lookup"><span data-stu-id="55413-102">Backup Options</span></span>
  <span data-ttu-id="55413-103">여러 가지 방법으로 데이터베이스를 백업할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 있으며, 모두 서버 관리자와 데이터베이스 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="55413-103">There are many ways to back up your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and they all require that you have server administrator and database administrator permissions.</span></span> <span data-ttu-id="55413-104">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **백업** 대화 상자를 열고 적절한 옵션 구성을 선택한 후 백업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-104">You can open the **Backup** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the appropriate options configuration, and then run the backup from the dialog box itself.</span></span> <span data-ttu-id="55413-105">또는 파일에 이미 지정된 설정을 사용하는 스크립트를 만들어 저장하고 필요할 때마다 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-105">Or, you can create a script using the settings already specified in the file; the script can then be saved and run as frequently as required.</span></span>  
  
## <a name="backup-and-synchronize"></a><span data-ttu-id="55413-106">백업 및 동기화</span><span class="sxs-lookup"><span data-stu-id="55413-106">Backup and Synchronize</span></span>  
 <span data-ttu-id="55413-107">데이터베이스가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]원격 인스턴스에 있는 경우 동기화 기능을 사용하여 데이터베이스를 로컬 인스턴스로 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-107">If the database is located on a remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the synchronization feature to back up the database to the local instance.</span></span> <span data-ttu-id="55413-108">이 방법으로 데이터베이스의 개발 빌드를 프로덕션으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-108">Development builds of a database can be moved into production in this manner.</span></span> <span data-ttu-id="55413-109">기존의 파일 기반 백업과 복원을 사용하여 개발 빌드를 프로덕션으로 이동할 수도 있으나 동기화를 사용하면 추가 기능을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-109">You can also use the conventional, file based, backup and restore to move the development build into production, but synchronization provides additional functionality.</span></span> <span data-ttu-id="55413-110">예를 들어 개발 컴퓨터와 프로덕션 컴퓨터의 보안 설정이 다른 경우 동기화를 사용하면 해당 설정을 유지하고 역할을 제외한 모든 개체를 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-110">For example, you can have security settings which are different for the development and production computers; synchronization will provide you the option to maintain those settings and synchronize all objects other than roles.</span></span> <span data-ttu-id="55413-111">또한 동기화는 일반적으로 원본 컴퓨터와 대상 컴퓨터에서 다른 개체에 대해 증분 업데이트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="55413-111">Also, synchronization typically does an incremental update of those objects which are different for the source and destination computers.</span></span> <span data-ttu-id="55413-112">백업/복원 기능으로는 이러한 증분 백업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55413-112">This kind of incremental backup is not available using the backup/restore feature.</span></span> <span data-ttu-id="55413-113">자세한 내용은 [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55413-113">For more information, see [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="55413-114">Analysis Services 서비스 계정에는 각 파일에 대해 지정한 백업 위치에 쓸 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55413-114">The Analysis Services service account must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="55413-115">또한 사용자는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 관리자 역할이나 백업할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버를 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55413-115">Also, the user must have one of the following roles: administrator role on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55413-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55413-116">See Also</span></span>  
 <span data-ttu-id="55413-117">[데이터베이스 백업 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="55413-117">[Backup Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="55413-118">[Analysis Services 데이터베이스 백업 및 복원](backup-and-restore-of-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="55413-118">[Backup and Restore of Analysis Services Databases](backup-and-restore-of-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="55413-119">[Backup 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="55413-119">[Backup Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) </span></span>  
 [<span data-ttu-id="55413-120">데이터베이스 백업, 복원 및 동기화&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="55413-120">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
