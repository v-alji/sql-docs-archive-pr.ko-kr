---
title: SQL Native Client 11.0 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client configuration [SQL Server], SQL Server Native Client
ms.assetid: e73143e9-5e7b-4d0a-8827-ab900efdcb35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 183dd2d161b1bf0b13140a607167b81dab086fdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647412"
---
# <a name="sql-native-client-110-configuration"></a><span data-ttu-id="0f53b-102">SQL Native Client 11.0 구성</span><span class="sxs-lookup"><span data-stu-id="0f53b-102">SQL Native Client 11.0 Configuration</span></span>
  <span data-ttu-id="0f53b-103">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 **SQL Server Native Client 구성** 대화 상자에 대한 F1 도움말 항목을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0f53b-103">This section contains the F1 Help topics for the **SQL Server Native Client Configuration** dialogs in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0f53b-104">Native Client는 클라이언트 컴퓨터가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]부터 시작하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결하는 데 사용하는 네트워크 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="0f53b-104">Native Client is the network library that client computers use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], starting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0f53b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 구성에서 구성한 설정은 클라이언트 프로그램이 실행되는 컴퓨터에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f53b-105">The settings configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Configuration, are used on the computer running the client program.</span></span> <span data-ttu-id="0f53b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실행되는 컴퓨터에서 구성한 경우 서버에서 실행되는 클라이언트 프로그램에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f53b-106">When configured on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they affect only those client programs running on the server.</span></span>  
  
 <span data-ttu-id="0f53b-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]부터 시작하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 같은 클라이언트 도구를 사용하지 않는다면 이러한 설정은 이전 버전의 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 연결하는 클라이언트에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f53b-107">These settings do not affect clients connecting to previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unless they are using the client tools starting with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f53b-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0f53b-108">In this Section</span></span>  
  
-   [<span data-ttu-id="0f53b-109">SQL Server Native Client 구성 속성&#40;플래그 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-109">SQL Server Native Client Configuration Properties &#40;Flags Tab&#41;</span></span>](../../../2014/tools/configuration-manager/sql-server-native-client-configuration-properties-flags-tab.md)  
  
-   [<span data-ttu-id="0f53b-110">클라이언트 프로토콜&#40;SQL Server 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-110">Client Protocols &#40;SQL Server Configuration Manager&#41;</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
    -   [<span data-ttu-id="0f53b-111">클라이언트 프로토콜 속성&#40;순서 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-111">Client Protocols Properties &#40;Order Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-properties-order-tab.md)  
  
    -   [<span data-ttu-id="0f53b-112">클라이언트 프로토콜 - 공유 메모리 속성&#40;프로토콜 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-112">Client Protocols - Shared Memory Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-shared-memory-properties-protocol-tab.md)  
  
    -   [<span data-ttu-id="0f53b-113">클라이언트 프로토콜-TCP 및 IP 속성 &#40;프로토콜 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-113">Client Protocols - TCP and IP Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-tcp-and-ip-properties-protocol-tab.md)  
  
    -   [<span data-ttu-id="0f53b-114">클라이언트 프로토콜 - 명명된 파이프 속성&#40;프로토콜 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-114">Client Protocols - Named Pipes Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-named-pipes-properties-protocol-tab.md)  
  
-   [<span data-ttu-id="0f53b-115">별칭&#40;SQL Server 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-115">Aliases &#40;SQL Server Configuration Manager&#41;</span></span>](../../../2014/tools/configuration-manager/aliases-sql-server-configuration-manager.md)  
  
    -   [<span data-ttu-id="0f53b-116">새 별칭&#40;별칭 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-116">New Alias &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)  
  
    -   [<span data-ttu-id="0f53b-117">&#60;Alias&#62; 속성&#40;별칭 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="0f53b-117">&#60;Alias&#62; Properties &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
    -   [<span data-ttu-id="0f53b-118">공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="0f53b-118">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
    -   [<span data-ttu-id="0f53b-119">TCP/IP를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="0f53b-119">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
    -   [<span data-ttu-id="0f53b-120">명명된 파이프를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="0f53b-120">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
