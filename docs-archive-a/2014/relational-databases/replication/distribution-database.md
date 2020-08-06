---
title: 배포 데이터베이스 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d98a80be52ae77cbdaf1581a5b3397f9d11af4fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646919"
---
# <a name="distribution-database"></a><span data-ttu-id="1efe0-102">배포 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="1efe0-102">Distribution Database</span></span>
  <span data-ttu-id="1efe0-103">배포 데이터베이스는 모든 유형의 복제에 대한 메타데이터 및 기록 데이터와 트랜잭션 복제에 대한 트랜잭션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-103">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span>  
  
 <span data-ttu-id="1efe0-104">대부분의 경우 배포 데이터베이스는 하나면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-104">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="1efe0-105">그러나 여러 게시자가 단일 배포자를 사용하는 경우에는 각 게시자에 대해 배포 데이터베이스를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="1efe0-105">However, if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="1efe0-106">이렇게 하면 각 배포 데이터베이스를 통한 데이터 흐름이 고유하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-106">Doing so ensures that the data flowing through each distribution database is distinct.</span></span> <span data-ttu-id="1efe0-107">배포 구성 마법사를 사용하여 배포자에 대한 배포 데이터베이스를 하나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-107">You can specify one distribution database for the Distributor using the Configure Distribution Wizard.</span></span> <span data-ttu-id="1efe0-108">필요한 경우 **배포자 속성** 대화 상자에서 추가 배포 데이터베이스를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="1efe0-108">If necessary, specify additional distribution databases in the **Distributor Properties** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1efe0-109">옵션</span><span class="sxs-lookup"><span data-stu-id="1efe0-109">Options</span></span>  
 <span data-ttu-id="1efe0-110">**배포 데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="1efe0-110">**Distribution database name**</span></span>  
 <span data-ttu-id="1efe0-111">배포 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-111">Enter a name for the distribution database.</span></span> <span data-ttu-id="1efe0-112">배포 데이터베이스의 기본 이름은 'distribution'입니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-112">The default name for the distribution database is 'distribution'.</span></span> <span data-ttu-id="1efe0-113">이름을 지정하는 경우 이름은 최대 128자가 될 수 있으며, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 내에서 고유해야 하고, 식별자 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-113">If you specify a name, the name can be a maximum of 128 characters, must be unique within an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and must conform to the rules for identifiers.</span></span> <span data-ttu-id="1efe0-114">자세한 내용은 [Database Identifiers](../databases/database-identifiers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1efe0-114">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
 <span data-ttu-id="1efe0-115">**배포 데이터베이스 파일 폴더** 및 **배포 데이터베이스 로그 파일 폴더**</span><span class="sxs-lookup"><span data-stu-id="1efe0-115">**Folder for the distribution database file** and **Folder for the distribution database log file**</span></span>  
 <span data-ttu-id="1efe0-116">배포 데이터베이스 및 로그 파일에 대한 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-116">Enter the path for the distribution database and log files.</span></span> <span data-ttu-id="1efe0-117">경로는 배포자에 로컬인 디스크여야 하므로 로컬 드라이브 문자와 콜론(예: C:)으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-117">Paths must refer to disks that are local to the Distributor and begin with a local drive letter and colon (for example, C:).</span></span> <span data-ttu-id="1efe0-118">매핑된 드라이브 문자와 네트워크 경로는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-118">Mapped drive letters and network paths are not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1efe0-119">배포 데이터베이스 로그를 배포 데이터베이스에서 별개의 디스크 드라이브에 두어 트랜잭션을 기록하는 데 걸리는 시간을 줄이고 복제 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe0-119">You can decrease the time it takes to write transactions and improve the performance of replication by placing the distribution database log on a separate disk drive from the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efe0-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1efe0-120">See Also</span></span>  
 <span data-ttu-id="1efe0-121">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="1efe0-121">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="1efe0-122">[게시 및 배포 구성](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="1efe0-122">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 [<span data-ttu-id="1efe0-123">배포자 및 게시자 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="1efe0-123">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)  
  
  
