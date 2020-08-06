---
title: Distributed Replay 클라이언트 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 53124029483c25ed7894b279283e1de02c647350
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660872"
---
# <a name="distributed-replay-client-configuration"></a><span data-ttu-id="cef79-102">Distributed Replay Client 구성</span><span class="sxs-lookup"><span data-stu-id="cef79-102">Distributed Replay Client Configuration</span></span>
  <span data-ttu-id="cef79-103">**설치 마법사의** Distributed Replay Client 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 페이지를 사용하여 Distributed Replay Client 서비스에 대한 관리 권한을 부여할 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-103">Use the **Distributed Replay Client Configuration** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the users you want to grant administrative permissions to for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="cef79-104">관리 권한이 있는 사용자는 Distributed Replay Client 서비스에 무제한으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-104">Users that have administrative permissions will have unlimited access to the Distributed Replay client service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cef79-105">옵션</span><span class="sxs-lookup"><span data-stu-id="cef79-105">Options</span></span>  
 <span data-ttu-id="cef79-106">**컨트롤러 이름**</span><span class="sxs-lookup"><span data-stu-id="cef79-106">**Controller Name**</span></span>  
 <span data-ttu-id="cef79-107">이 매개 변수는 선택적 매개 변수 이며 기본값은 \<*blank*> 입니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-107">This is an optional parameter, and the default value is \<*blank*>.</span></span>  
  
 <span data-ttu-id="cef79-108">클라이언트 컴퓨터에서 Distributed Replay Client 서비스를 위해 통신할 컨트롤러의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-108">Enter the name of the controller that the client computer will communicate with for the Distributed Replay client service.</span></span> <span data-ttu-id="cef79-109">다음 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="cef79-109">Note the following:</span></span>  
  
-   <span data-ttu-id="cef79-110">이는 FQDN(정규화된 도메인 이름)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-110">The name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="cef79-111">예를 들어, Microsoft의 제품 계층에서 server1이라는 호스트의 FQDN은 server1.products.microsoft.com일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-111">For example, a host called server1 in the products hierarchy at Microsoft may have an FQDN of server1.products.microsoft.com.</span></span>  
  
-   <span data-ttu-id="cef79-112">컨트롤러를 이미 설정한 경우 각 클라이언트를 구성할 때 컨트롤러의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-112">If you have already set up a controller, enter the name of the controller while configuring each client.</span></span>  
  
-   <span data-ttu-id="cef79-113">컨트롤러를 아직 설정하지 않은 경우에는 컨트롤러 이름을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-113">If you have net yet set up a controller, you can leave the controller name blank.</span></span> <span data-ttu-id="cef79-114">그러나 **클라이언트 구성** 파일에서 컨트롤러 이름을 수동으로 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-114">However, you must manually enter the controller name in the **client configuration** file.</span></span>  
  
 <span data-ttu-id="cef79-115">**작업 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="cef79-115">**Working Directory**</span></span>  
 <span data-ttu-id="cef79-116">Distributed Replay Client 서비스의 작업 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-116">Specify the working directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="cef79-117">기본 작업 디렉터리는 \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\입니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-117">The default working directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.</span></span>  
  
 <span data-ttu-id="cef79-118">**결과 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="cef79-118">**Result Directory**</span></span>  
 <span data-ttu-id="cef79-119">Distributed Replay Client 서비스의 결과 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-119">Specify the result directory for the Distributed Replay client service.</span></span>  
  
 <span data-ttu-id="cef79-120">기본 결과 디렉터리는 \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\입니다.</span><span class="sxs-lookup"><span data-stu-id="cef79-120">The default result directory is \<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.</span></span>  
  
  
