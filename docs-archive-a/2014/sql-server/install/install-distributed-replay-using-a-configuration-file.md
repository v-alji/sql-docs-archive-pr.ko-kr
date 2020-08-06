---
title: 구성 파일을 사용 하 여 Distributed Replay 설치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7757cce29c2e6b3ce4f1e91fc97cbf8be02ae521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735896"
---
# <a name="install-distributed-replay-using-a-configuration-file"></a><span data-ttu-id="bfe63-102">구성 파일을 사용하여 Distributed Replay 설치</span><span class="sxs-lookup"><span data-stu-id="bfe63-102">Install Distributed Replay Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bfe63-103">설치 시 사용자 입력 및 시스템 기본값을 기반으로 구성 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-103">Setup provides the ability to generate a configuration file based on user input and system defaults.</span></span> <span data-ttu-id="bfe63-104">관리 도구를 설치하도록 지정한 경우 이 구성 파일을 사용하여 세 가지 Distributed Replay 구성 요소(관리 도구, Distributed Replay Controller 및 Distributed Replay Client)를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-104">If you specify that you want the Management tools installed, you can use the configuration file to deploy the three Distributed Replay components (administration tool, Distributed Replay controller, and the Distributed Replay client).</span></span> <span data-ttu-id="bfe63-105">구성 파일을 사용하면 Distributed Replay 구성 요소를 설치, 복구 및 다시 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-105">It supports Installing, repairing, and uninstalling of the Distributed Replay components.</span></span>  
  
 <span data-ttu-id="bfe63-106">구성 파일은 명령줄에서 설치할 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-106">Setup supports the use of the configuration file only through the command-line.</span></span> <span data-ttu-id="bfe63-107">구성 파일을 사용할 때 매개 변수의 처리 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="bfe63-108">구성 파일이 패키지의 기본값을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="bfe63-109">명령줄 값이 구성 파일의 값을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="bfe63-110">구성 파일을 사용 하는 방법에 대 한 자세한 내용은 [구성 파일을 사용 하 여 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfe63-110">For more information about how to use a configuration file, see [Install SQL Server 2014 Using a Configuration File](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bfe63-111">Distributed Replay를 설치한 후에는 컨트롤러 및 클라이언트 컴퓨터에서 방화벽 규칙을 만들고 각 클라이언트 컴퓨터에 대상 서버에 대한 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-111">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="bfe63-112">자세한 내용은 [설치 후 단계 완료](../../tools/distributed-replay/complete-the-post-installation-steps.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfe63-112">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
### <a name="to-generate-a-configuration-file"></a><span data-ttu-id="bfe63-113">구성 파일을 생성하려면</span><span class="sxs-lookup"><span data-stu-id="bfe63-113">To generate a configuration file</span></span>  
  
1.  <span data-ttu-id="bfe63-114">설치 마법사의 안내에 따르면 **설치 준비 완료** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-114">Follow the Setup wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="bfe63-115">구성 파일의 경로는 **설치 준비 완료** 페이지의 구성 파일 경로 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-115">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span>  
  
2.  <span data-ttu-id="bfe63-116">설치를 실제로 완료하지는 않고 INI 파일을 생성하기 위해 설치를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-116">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
### <a name="to-install-distributed-replay-using-the-configuration-file"></a><span data-ttu-id="bfe63-117">구성 파일을 사용하여 Distributed Replay를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="bfe63-117">To Install Distributed Replay Using the Configuration File</span></span>  
  
-   <span data-ttu-id="bfe63-118">명령 프롬프트에서 설치를 실행하고 ConfigurationFile 매개 변수를 사용하여 ConfigurationFile.ini를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-118">Run the installation through the command prompt and supply the ConfigurationFile.ini using the ConfigurationFile parameter.</span></span>  
  
 <span data-ttu-id="bfe63-119">**예제 구문**</span><span class="sxs-lookup"><span data-stu-id="bfe63-119">**Sample Syntax**</span></span>  
  
 <span data-ttu-id="bfe63-120">다음 예에서는 명령 프롬프트에서 구성 파일을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-120">Following is an example on how to specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bfe63-121">구성 파일에서는 암호를 구성할 수 없으므로 명령줄에서 두 암호를 모두 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfe63-121">You must specify both passwords in the command line because you cannot configure them in the configuration file.</span></span>  
  
  
