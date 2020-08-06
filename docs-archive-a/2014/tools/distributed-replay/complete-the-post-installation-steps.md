---
title: 설치 후 단계를 완료 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1e9aae3dccaa409bcebc473213286f3edf19e7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651953"
---
# <a name="complete-the-post-installation-steps"></a><span data-ttu-id="03657-102">설치 후 단계 완료</span><span class="sxs-lookup"><span data-stu-id="03657-102">Complete the Post-Installation Steps</span></span>
  <span data-ttu-id="03657-103">Distributed Replay를 설치한 후에는 Distributed Replay Controller 및 Client 서비스 계정을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03657-103">After you install Distributed Replay you must modify the Distributed Replay controller and client services accounts.</span></span>  
  
### <a name="to-complete-the-post-installation-steps"></a><span data-ttu-id="03657-104">설치 후 단계를 완료하려면</span><span class="sxs-lookup"><span data-stu-id="03657-104">To complete the post-installation steps</span></span>  
  
1.  <span data-ttu-id="03657-105">**방화벽 규칙 만들기**: 컨트롤러 및 클라이언트 컴퓨터에서 해당 서비스에 대해 방화벽을 통과하는 인바운드 트래픽을 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03657-105">**Create firewall rules**: On the controller and client computers, you must allow inbound traffic through the firewall for the corresponding service.</span></span> <span data-ttu-id="03657-106">서비스 실행 파일에 대해 방화벽 규칙을 지정합니다. 이 파일은 설치 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03657-106">Specify the firewall rules for the service executables, located in the installation folders.</span></span>  
  
    1.  <span data-ttu-id="03657-107">컨트롤러 서비스의 경우 설치 폴더에 있는 **DReplayController.exe**에 대해 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="03657-107">For the controller service, create a rule for **DReplayController.exe**, located in the installation folder.</span></span> <span data-ttu-id="03657-108">예를 들어 다음 명령은 이 규칙을 설정하며 여기서 `%InstallPath%` 는 서비스 설치 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="03657-108">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  <span data-ttu-id="03657-109">클라이언트 서비스의 경우 각 클라이언트 컴퓨터에서 설치 폴더에 있는 **DReplayClient.exe**에 대해 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="03657-109">For the client service, on each client computer, create a rule for **DReplayClient.exe**, located in the installation folder.</span></span> <span data-ttu-id="03657-110">예를 들어 다음 명령은 이 규칙을 설정하며 여기서 `%InstallPath%` 는 서비스 설치 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="03657-110">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  <span data-ttu-id="03657-111">**대상 서버에서 각 클라이언트 권한 부여**: 클라이언트 컴퓨터에 클라이언트 서비스를 설치하는 작업을 완료하면 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 sysadmin 역할에 클라이언트 서비스 계정을 수동으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03657-111">**Grant each client permissions on the target server**: After you have completed installing the client service on the client computers, you must manually add the client service accounts to the sysadmin role on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="03657-112">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="03657-112">.NET Framework Security</span></span>  
 <span data-ttu-id="03657-113">Distributed Replay 기능을 설치하려면 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03657-113">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="03657-114">sysadmin 권한을 가진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인만 테스트 서버의 sysadmin 서버 역할에 클라이언트 서비스 계정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03657-114">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="03657-115">Distributed Replay 보안 고려 사항에 대한 자세한 내용은 [Distributed Replay Security](distributed-replay-security.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="03657-115">For more information about Distributed Replay security considerations, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
  
