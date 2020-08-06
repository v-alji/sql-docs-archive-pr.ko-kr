---
title: 클라이언트 프로토콜 속성 (순서 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client protocols [SQL Server]
ms.assetid: 64fd7135-1756-4885-bed9-9ab8997ecc6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a367cff3495389d1a707ed108ba75e1e736538b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729968"
---
# <a name="client-protocols-properties-order-tab"></a><span data-ttu-id="e7fe4-102">클라이언트 프로토콜 속성(순서 탭)</span><span class="sxs-lookup"><span data-stu-id="e7fe4-102">Client Protocols Properties (Order Tab)</span></span>
  <span data-ttu-id="e7fe4-103">**클라이언트 프로토콜 속성**대화 상자의 **순서** 페이지를 사용하여 클라이언트 프로토콜을 확인하고 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-103">Use the **Order**page on the **Client Protocols Properties** dialog box to view and enable the client protocols.</span></span>  
  
 <span data-ttu-id="e7fe4-104">선택한 프로토콜을 **사용할 수 없는 프로토콜** 또는 **사용할 수 있는 프로토콜** 목록으로 이동하려면 해당 프로토콜을 클릭한 다음 **사용** 또는 **사용 안 함** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-104">Click a protocol, and then click **Enable** or **Disable** to move the selected protocol to the **Disabled Protocols** or **Enabled Protocols** list.</span></span>  
  
 <span data-ttu-id="e7fe4-105">목록의 맨 위에 있는 프로토콜에 먼저 연결을 시도한 다음 두 번째 프로토콜에 연결하는 식으로 목록에 나오는 순서대로 연결 시도가 진행됩니다. 위쪽 화살표 단추나 아래쪽 화살표 단추를 클릭하여 **사용할 수 있는 프로토콜** 목록의 위나 아래로 프로토콜을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-105">Protocols are tried in the order listed, attempting to connect using the top protocol first, and then the second listed protocol, etc. Move protocols up or down the **Enabled Protocols** list, by clicking the up arrow and down arrow buttons.</span></span> <span data-ttu-id="e7fe4-106">서버와 동일한 컴퓨터에서 실행되는 클라이언트가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 때는 **공유 메모리** 프로토콜을 맨 먼저 사용합니다(사용하는 경우).</span><span class="sxs-lookup"><span data-stu-id="e7fe4-106">When connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer, the **Shared Memory** protocol will always be tried first, if enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7fe4-107">이러한 설정은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-107">These settings are not used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET SqlClient.</span></span> <span data-ttu-id="e7fe4-108">.NET SqlClient에 대한 프로토콜 순서는 첫 번째가 TCP이고 그 다음이 명명된 파이프이며 이 순서는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-108">The protocol order for .NET SqlClient is first TCP, and then named pipes, which cannot be changed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7fe4-109">옵션</span><span class="sxs-lookup"><span data-stu-id="e7fe4-109">Options</span></span>  
 <span data-ttu-id="e7fe4-110">**사용**</span><span class="sxs-lookup"><span data-stu-id="e7fe4-110">**Disabled Protocols**</span></span>  
 <span data-ttu-id="e7fe4-111">설치되어 있지만 현재 사용되지 않는 프로토콜을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-111">Lists protocols which are installed but are not currently used.</span></span>  
  
 <span data-ttu-id="e7fe4-112">**사용 안 함**</span><span class="sxs-lookup"><span data-stu-id="e7fe4-112">**Enabled Protocols**</span></span>  
 <span data-ttu-id="e7fe4-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)]이 컴퓨터의 클라이언트에 사용할 수 있는 프로토콜을 나열 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-113">Lists protocols which are available for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this computer.</span></span>  
  
 **>**  
 <span data-ttu-id="e7fe4-114">**사용할 수 없는 프로토콜** 상자에서 선택한 프로토콜을 **사용할 수 있는 프로토콜** 상자로 이동하여 사용할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-114">Enables the currently highlighted protocol in the **Disabled Protocols** box, moving it to the **Enabled Protocols** box.</span></span>  
  
 **\<**  
 <span data-ttu-id="e7fe4-115">**사용할 수 있는 프로토콜** 상자에서 선택한 프로토콜을 **사용할 수 없는 프로토콜** 상자로 이동하여 사용할 수 없도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-115">Disables the currently highlighted protocol in the **Enabled Protocols** box, moving it to the **Disabled Protocols** box.</span></span>  
  
 <span data-ttu-id="e7fe4-116">위쪽 화살표</span><span class="sxs-lookup"><span data-stu-id="e7fe4-116">Up arrow</span></span>  
 <span data-ttu-id="e7fe4-117">목록에서 선택한 프로토콜을 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-117">Moves the highlighted protocol up in the list.</span></span> <span data-ttu-id="e7fe4-118">이렇게 하면 연결할 때 Net-Library에서 해당 프로토콜을 먼저 사용하도록 프로토콜의 우선 순위를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-118">This allows you to increase the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="e7fe4-119">아래쪽 화살표</span><span class="sxs-lookup"><span data-stu-id="e7fe4-119">Down arrow</span></span>  
 <span data-ttu-id="e7fe4-120">목록에서 선택한 프로토콜을 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-120">Moves the highlighted protocol down in the list.</span></span> <span data-ttu-id="e7fe4-121">이렇게 하면 연결할 때 Net-Library에서 해당 프로토콜을 나중에 사용하도록 프로토콜의 우선 순위를 낮출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-121">This allows you to decrease the priority in which the Net-Library will attempt to use the selected protocol for connections.</span></span>  
  
 <span data-ttu-id="e7fe4-122">**공유 메모리 프로토콜 사용**</span><span class="sxs-lookup"><span data-stu-id="e7fe4-122">**Enable Shared Memory Protocol**</span></span>  
 <span data-ttu-id="e7fe4-123">서버와 동일한 컴퓨터에서 실행되는 클라이언트가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결할 때 항상 맨 먼저 연결을 시도하는 공유 메모리 프로토콜을 설정합니다(사용하는 경우).</span><span class="sxs-lookup"><span data-stu-id="e7fe4-123">Enables the shared memory protocol which is always tried first (if enabled), when connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client on that computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7fe4-124">접두사를 통해 또는 연결 문자열의 일부로 프로토콜을 지정하면 지정한 프로토콜에 대해서만 연결이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7fe4-124">If the protocol is specified through a prefix or as part of the connection string, only the specified protocol is attempted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fe4-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7fe4-125">See Also</span></span>  
 [<span data-ttu-id="e7fe4-126">네트워크 프로토콜 선택</span><span class="sxs-lookup"><span data-stu-id="e7fe4-126">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
