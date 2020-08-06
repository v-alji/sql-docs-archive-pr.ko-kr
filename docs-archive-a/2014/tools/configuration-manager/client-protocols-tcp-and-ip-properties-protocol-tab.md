---
title: 클라이언트 프로토콜-TCP 및 IP 속성 (프로토콜 탭) | Microsoft Docs
description: 연결 유지 매개 변수 및 기본 포트 번호와 같은 Microsoft SQL Server Configuration Manager에서 TCP/IP 옵션을 지정 하는 방법에 대해 알아봅니다.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: rothja
ms.author: jroth
ms.openlocfilehash: dfcf0348dc863970384a40cc9e773481adeedb35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737359"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a><span data-ttu-id="c0059-103">클라이언트 프로토콜 - TCP/IP 속성(프로토콜 탭)</span><span class="sxs-lookup"><span data-stu-id="c0059-103">Client Protocols - TCP and IP Properties (Protocol Tab)</span></span>
  <span data-ttu-id="c0059-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **TCP/IP 속성** 대화 상자의 **프로토콜** 탭을 사용하여 다음 옵션을 확인 또는 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-104">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, use the **Protocol** tab on the **TCP/IP Properties** dialog box to view or specify the following options.</span></span> <span data-ttu-id="c0059-105">다른 포트에 연결하려면 **기본 포트** 입력란에 포트 번호를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0059-105">To connect to a different port, type the port number in the **Default Port** box.</span></span> <span data-ttu-id="c0059-106">연결 문자열에 대한 자세한 내용은 [TCP/IP를 사용하여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0059-106">For more information about connection strings, see [Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0059-107">옵션</span><span class="sxs-lookup"><span data-stu-id="c0059-107">Options</span></span>  
 <span data-ttu-id="c0059-108">**기본 포트**</span><span class="sxs-lookup"><span data-stu-id="c0059-108">**Default Port**</span></span>  
 <span data-ttu-id="c0059-109">대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결할 때 TCP/IP Net-library가 사용할 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-109">Specifies the port that the TCP/IP Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c0059-110">기본 포트는 1433입니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-110">The default value port is 1433.</span></span>  
  
 <span data-ttu-id="c0059-111">클라이언트에서는 [!INCLUDE[ssDE](../../includes/ssde-md.md)]기본 인스턴스로 연결할 때 이 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-111">When connecting to a default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client uses this value.</span></span> <span data-ttu-id="c0059-112">기본 인스턴스가 다른 포트를 수신하도록 구성된 경우 이 값을 해당 포트 번호로 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0059-112">If a default instance has been configured to listen on a different port, change this value to that port number.</span></span>  
  
 <span data-ttu-id="c0059-113">클라이언트는 명명된 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스로 연결할 때 서버 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스에서 포트 번호 가져오기를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-113">When connecting to a named instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client will attempt to obtain the port number from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service running on the server computer.</span></span> <span data-ttu-id="c0059-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스가 실행되지 않는 경우 이 설정 또는 연결 문자열의 일부로 포트 번호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-114">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service is not running, the port number must be provided through this setting, or as part of the connection string.</span></span>  
  
 <span data-ttu-id="c0059-115">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="c0059-115">**Enabled**</span></span>  
 <span data-ttu-id="c0059-116">가능한 값은 **예** 및 **아니요**입니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-116">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="c0059-117">**활성 유지**</span><span class="sxs-lookup"><span data-stu-id="c0059-117">**Keep Alive**</span></span>  
 <span data-ttu-id="c0059-118">이 매개 변수(밀리초)는 연결을 유지하기 위해 TCP에서 **KEEPALIVE** 패킷을 보내는 빈도를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-118">This parameter (in milliseconds) controls how often TCP attempts to verify that an idle connection is still intact by sending a **KEEPALIVE** packet.</span></span> <span data-ttu-id="c0059-119">기본값은 30000밀리초입니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-119">The default is 30000 milliseconds.</span></span>  
  
 <span data-ttu-id="c0059-120">**연결 유지 간격**</span><span class="sxs-lookup"><span data-stu-id="c0059-120">**Keep Alive Interval**</span></span>  
 <span data-ttu-id="c0059-121">이 매개 변수(밀리초)는 응답을 받을 때까지 **KEEPALIVE** 재전송을 구분하는 간격을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-121">This parameter (in milliseconds) determines the interval separating **KEEPALIVE** retransmissions until a response is received.</span></span> <span data-ttu-id="c0059-122">기본값은 1000밀리초입니다.</span><span class="sxs-lookup"><span data-stu-id="c0059-122">The default is 1000 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0059-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0059-123">See Also</span></span>  
 <span data-ttu-id="c0059-124">[네트워크 프로토콜 선택](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="c0059-124">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 <span data-ttu-id="c0059-125">[새 별칭 &#40;별칭 탭&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span><span class="sxs-lookup"><span data-stu-id="c0059-125">[New Alias &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span></span>  
 [<span data-ttu-id="c0059-126">&#60;Alias&#62; 속성&#40;별칭 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c0059-126">&#60;Alias&#62; Properties &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
