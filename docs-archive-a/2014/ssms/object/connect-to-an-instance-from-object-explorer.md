---
title: 개체 탐색기에서 인스턴스에 연결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: stevestein
ms.author: sstein
ms.openlocfilehash: 918dd3ed6e8eb765f2cb7077107407c324c51a4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638534"
---
# <a name="connect-to-an-instance-from-object-explorer"></a><span data-ttu-id="7de15-102">개체 탐색기에서 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="7de15-102">Connect to an Instance From Object Explorer</span></span>
  <span data-ttu-id="7de15-103">개체 탐색기를 사용하여 개체를 관리하려면 먼저 개체가 포함된 인스턴스에 개체 탐색기를 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-103">To manage objects by using Object Explorer, you must first connect Object Explorer to the instance that contains the objects.</span></span> <span data-ttu-id="7de15-104">동시에 여러 인스턴스에 개체 탐색기를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-104">You can connect Object Explorer to multiple instances at the same time.</span></span>  
  
## <a name="connecting-object-explorer-to-a-server"></a><span data-ttu-id="7de15-105">개체 탐색기를 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="7de15-105">Connecting Object Explorer to a Server</span></span>  
 <span data-ttu-id="7de15-106">개체 탐색기를 사용하려면 먼저 서버에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-106">To use Object Explorer you must first connect to a server.</span></span> <span data-ttu-id="7de15-107">개체 탐색기 도구 모음에서 **연결** 을 클릭하고 드롭다운 목록에서 서버의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-107">Click **Connect** on the Object Explorer toolbar and choose the type of server from the drop-down list.</span></span> <span data-ttu-id="7de15-108">**서버에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-108">The **Connect to Server** dialog box opens.</span></span> <span data-ttu-id="7de15-109">연결하려면 적어도 서버 이름과 올바른 인증 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-109">To connect, you must provide at least the name of the server and the correct authentication information.</span></span>  
  
## <a name="optional-object-explorer-connection-settings"></a><span data-ttu-id="7de15-110">개체 탐색기 연결 설정(옵션)</span><span class="sxs-lookup"><span data-stu-id="7de15-110">Optional Object Explorer Connection Settings</span></span>  
 <span data-ttu-id="7de15-111">서버에 연결할 때 **서버에 연결** 대화 상자에서 추가 연결 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-111">When connecting to a server, you can specify additional connection information in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="7de15-112">**서버에 연결** 대화 상자는 마지막으로 사용된 설정을 보유하며 새 코드 편집기 창과 같은 새 연결에서 이러한 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-112">The **Connect to Server** dialog box will retain the last used settings, and new connections, such as new code editor windows, will use those settings.</span></span>  
  
 <span data-ttu-id="7de15-113">연결 설정(옵션)을 지정하려면 다음 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="7de15-113">To specify optional connection settings, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7de15-114">개체 탐색기 도구 모음에서 **연결** 을 클릭하고 연결할 서버의 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-114">Click **Connect** on the Object Explorer toolbar, and click the type of server to connect to.</span></span> <span data-ttu-id="7de15-115">**서버에 연결** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-115">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="7de15-116">**서버 이름** 상자에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-116">In the **Server Name** box, type the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
3.  <span data-ttu-id="7de15-117">**옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-117">Click **Options**.</span></span> <span data-ttu-id="7de15-118">**서버에 연결** 대화 상자에 추가 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-118">The **Connect to Server** dialog box displays additional options.</span></span>  
  
4.  <span data-ttu-id="7de15-119">**연결 속성** 탭을 클릭하여 추가 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-119">Click the **Connection Properties** tab to configure the additional settings.</span></span> <span data-ttu-id="7de15-120">사용할 수 있는 설정은 서버 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-120">The settings that are available vary depending upon the server type.</span></span> <span data-ttu-id="7de15-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]의 경우 다음 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-121">The following settings are available for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
    |<span data-ttu-id="7de15-122">Setting</span><span class="sxs-lookup"><span data-stu-id="7de15-122">Setting</span></span>|<span data-ttu-id="7de15-123">설명</span><span class="sxs-lookup"><span data-stu-id="7de15-123">Description</span></span>|  
    |-------------|-----------------|  
    |<span data-ttu-id="7de15-124">**데이터베이스에 연결**</span><span class="sxs-lookup"><span data-stu-id="7de15-124">**Connect to database**</span></span>|<span data-ttu-id="7de15-125">서버에서 사용할 수 있는 데이터베이스 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-125">Choose from the available databases on the server.</span></span> <span data-ttu-id="7de15-126">사용자에게 볼 수 있는 권한이 있는 데이터베이스만 이 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-126">This list will only show databases that you have permission to view.</span></span>|  
    |<span data-ttu-id="7de15-127">**네트워크 프로토콜**</span><span class="sxs-lookup"><span data-stu-id="7de15-127">**Network protocol**</span></span>|<span data-ttu-id="7de15-128">공유 메모리, TCP/IP 또는 명명된 파이프 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-128">Select from Shared Memory, TCP/IP, or Named Pipes.</span></span>|  
    |<span data-ttu-id="7de15-129">**네트워크 패킷 크기**</span><span class="sxs-lookup"><span data-stu-id="7de15-129">**Network packet size**</span></span>|<span data-ttu-id="7de15-130">바이트 단위로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-130">Configure in bytes.</span></span> <span data-ttu-id="7de15-131">기본 설정은 4096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-131">The default setting is 4096 bytes.</span></span>|  
    |<span data-ttu-id="7de15-132">**연결 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="7de15-132">**Connection timeout**</span></span>|<span data-ttu-id="7de15-133">초 단위로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-133">Configure in seconds.</span></span> <span data-ttu-id="7de15-134">기본 설정은 15초입니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-134">The default setting is 15 seconds.</span></span>|  
    |<span data-ttu-id="7de15-135">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="7de15-135">**Execution timeout**</span></span>|<span data-ttu-id="7de15-136">초 단위로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-136">Configure in seconds.</span></span> <span data-ttu-id="7de15-137">기본 설정(0)은 실행의 제한 시간이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-137">The default setting (0) indicates that execution will never time out.</span></span>|  
    |<span data-ttu-id="7de15-138">**연결 암호화**</span><span class="sxs-lookup"><span data-stu-id="7de15-138">**Encrypt connection**</span></span>|<span data-ttu-id="7de15-139">강제로 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-139">Forces encryption.</span></span>|  
  
5.  <span data-ttu-id="7de15-140">지정된 서버를 등록된 서버 목록에 추가하려면 **등록된 서버** 탭을 클릭하고 새 서버를 표시할 위치를 클릭한 다음 연결을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-140">To add the specified server to your list of registered servers, click the **Registered Server** tab, click on the location where you want the new server to appear, and then complete the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7de15-141">**추가 연결 매개 변수** 페이지를 사용하면 연결 문자열에 연결 매개 변수를 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7de15-141">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span> <span data-ttu-id="7de15-142">자세한 내용은 [서버에 연결&#40;추가 연결 매개 변수 페이지&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7de15-142">For more information, see [Connect to Server &#40;Additional Connection Parameters Page&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md).</span></span>  
  
  
