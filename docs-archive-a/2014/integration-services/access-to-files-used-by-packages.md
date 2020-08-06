---
title: 패키지에서 사용 하는 파일에 대 한 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db9511c91c9f229b7002f5b16cf077910a4ccf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647825"
---
# <a name="access-to-files-used-by-packages"></a><span data-ttu-id="1dda3-102">패키지에서 사용되는 파일 액세스</span><span class="sxs-lookup"><span data-stu-id="1dda3-102">Access to Files Used by Packages</span></span>
  <span data-ttu-id="1dda3-103">패키지 보호 수준은 패키지 외부에 저장된 파일을 보호하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-103">The package protection level does not protect files that are stored outside the package.</span></span> <span data-ttu-id="1dda3-104">이러한 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-104">These files include the following:</span></span>  
  
-   <span data-ttu-id="1dda3-105">구성 파일</span><span class="sxs-lookup"><span data-stu-id="1dda3-105">Configuration files</span></span>  
  
-   <span data-ttu-id="1dda3-106">검사점 파일</span><span class="sxs-lookup"><span data-stu-id="1dda3-106">Checkpoint files</span></span>  
  
-   <span data-ttu-id="1dda3-107">로그 파일</span><span class="sxs-lookup"><span data-stu-id="1dda3-107">Log files</span></span>  
  
 <span data-ttu-id="1dda3-108">이러한 파일은 특히 중요한 정보를 포함하고 있을 경우 별도로 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-108">These files must be protected separately, especially if they include sensitive information.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1dda3-109">구성 파일</span><span class="sxs-lookup"><span data-stu-id="1dda3-109">Configuration Files</span></span>  
 <span data-ttu-id="1dda3-110">구성에 로그인 및 암호 정보와 같은 중요한 정보가 포함된 경우 구성을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 저장하거나 ACL(액세스 제어 목록)을 사용하여 파일이 저장된 위치나 폴더에 대한 액세스를 제한하고 특정 계정에만 액세스할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-110">If you have sensitive information in a configuration, such as login and password information, you should consider saving the configuration to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or use an access control list (ACL) to restrict access to the location or folder where you store the files and allow access only to certain accounts.</span></span> <span data-ttu-id="1dda3-111">일반적으로 패키지를 실행하도록 허용할 계정이나 구성, 검사점 및 로그 파일의 내용에 대한 검토를 비롯하여 패키지를 관리하고 문제를 해결하는 계정에 대해 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-111">Typically, you would grant access to the accounts that you permit to run packages, and to the accounts that manage and troubleshoot packages, which may include reviewing the contents of configuration, checkpoint, and log files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1dda3-112">는 서버 및 데이터베이스 수준에서 보호하므로 보다 안전한 스토리지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-112">provides the more secure storage because it offers protection at the server and database levels.</span></span> <span data-ttu-id="1dda3-113">구성을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 저장하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 유형을 사용하고</span><span class="sxs-lookup"><span data-stu-id="1dda3-113">To save configurations to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type.</span></span> <span data-ttu-id="1dda3-114">파일 시스템을 저장하려면 XML 구성 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-114">To save to the file system, you use the XML configuration type.</span></span>  
  
 <span data-ttu-id="1dda3-115">자세한 내용은 [패키지 구성](../../2014/integration-services/package-configurations.md), [패키지 구성 만들기](../../2014/integration-services/create-package-configurations.md)및 [SQL Server 설치에 대한 보안 고려 사항](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dda3-115">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md), [Create Package Configurations](../../2014/integration-services/create-package-configurations.md), and [Security Considerations for a SQL Server Installation](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).</span></span>  
  
## <a name="checkpoint-files"></a><span data-ttu-id="1dda3-116">검사점 파일</span><span class="sxs-lookup"><span data-stu-id="1dda3-116">Checkpoint Files</span></span>  
 <span data-ttu-id="1dda3-117">이와 비슷하게 패키지에서 사용되는 검사점 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-117">Similarly, if the checkpoint file that the package uses includes sensitive information, you should use an access control list (ACL) to secure the location or folder where you store the file.</span></span> <span data-ttu-id="1dda3-118">검사점 파일은 패키지 진행 중에 현재 상태 정보와 현재 변수 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-118">Checkpoint files save current state information on the progress of the package as well as the current values of variables.</span></span> <span data-ttu-id="1dda3-119">예를 들어 패키지에는 전화 번호가 포함된 사용자 지정 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-119">For example, the package may include a custom variable that contains a telephone number.</span></span> <span data-ttu-id="1dda3-120">자세한 내용은 [검사점을 사용하여 패키지 다시 시작](packages/restart-packages-by-using-checkpoints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dda3-120">For more information, see [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).</span></span>  
  
## <a name="log-files"></a><span data-ttu-id="1dda3-121">로그 파일</span><span class="sxs-lookup"><span data-stu-id="1dda3-121">Log Files</span></span>  
 <span data-ttu-id="1dda3-122">파일 시스템에 기록된 로그 항목도 ACL(액세스 제어 목록)을 사용하여 보호되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-122">Log entries that are written to the file system should also be secured using an access control list (ACL).</span></span> <span data-ttu-id="1dda3-123">로그 항목을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블에 저장하고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 보안으로 보호할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-123">Log entries can also be stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables and protected by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="1dda3-124">로그 항목에는 중요한 정보가 포함될 수 있습니다. 예를 들어 패키지에 전화 번호를 참조하는 SQL 문을 구성하는 SQL 실행 태스크가 포함되는 경우 SQL 문에 대한 로그 항목에는 전화 번호가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-124">Log entries may include sensitive information, For example, if the package contains an Execute SQL task that constructs an SQL statement that refers to a telephone number, the log entry for the SQL statement includes the telephone number.</span></span> <span data-ttu-id="1dda3-125">SQL 문은 또한 데이터베이스에 있는 테이블 및 열 이름에 대한 개인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1dda3-125">The SQL statement may also reveal private information about table and column names in databases.</span></span> <span data-ttu-id="1dda3-126">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](performance/integration-services-ssis-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dda3-126">For more information, see [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md).</span></span>  
  
  
