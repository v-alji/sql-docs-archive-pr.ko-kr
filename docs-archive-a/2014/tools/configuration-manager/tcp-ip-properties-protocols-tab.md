---
title: TCP/IP 속성 (프로토콜 탭) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d5bc28faddae9a86a6636b56b907b57a2d8711a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646791"
---
# <a name="tcp---ip-properties-protocols-tab"></a><span data-ttu-id="b6e44-102">TCP/IP 속성 (프로토콜 탭)</span><span class="sxs-lookup"><span data-stu-id="b6e44-102">TCP - IP Properties (Protocols Tab)</span></span>
  <span data-ttu-id="b6e44-103">**TCP/IP 속성** 대화 상자를 사용하여 TCP/IP 프로토콜 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-103">Use the **TCP/IP Properties** dialog box to configure the options for the TCP/IP protocol.</span></span> <span data-ttu-id="b6e44-104">세부 정보 창에 개별 IP 주소 구성을 표시하려면 왼쪽 창에서 **TCP/IP** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-104">Click **TCP/IP** in the left pane, to show individual IP address configurations in the details pane.</span></span>  
  
 <span data-ttu-id="b6e44-105">변경 내용을 적용하려면 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-105">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted before the changes take effect.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6e44-106">옵션</span><span class="sxs-lookup"><span data-stu-id="b6e44-106">Options</span></span>  
 <span data-ttu-id="b6e44-107">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="b6e44-107">**Enabled**</span></span>  
 <span data-ttu-id="b6e44-108">가능한 값은 **예** 및 **아니요**입니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-108">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="b6e44-109">**Keep Alive**</span><span class="sxs-lookup"><span data-stu-id="b6e44-109">**Keep Alive**</span></span>  
 <span data-ttu-id="b6e44-110">연결의 원격 끝에 있는 컴퓨터가 사용 가능한지 확인하기 위해 연결 유지 패킷이 전송되는 간격(밀리초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-110">Specify the interval (milliseconds) in which keep-alive packets are transmitted to verify that the computer at the remote end of a connection is still available.</span></span>  
  
 <span data-ttu-id="b6e44-111">**Listen All**</span><span class="sxs-lookup"><span data-stu-id="b6e44-111">**Listen All**</span></span>  
 <span data-ttu-id="b6e44-112">SQL Server가 컴퓨터의 네트워크 카드에 바인딩된 모든 IP 주소를 수신하는지의 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-112">Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer.</span></span> <span data-ttu-id="b6e44-113">**아니요**로 설정된 경우 각 IP 주소의 속성 대화 상자를 사용하여 별도로 각 IP 주소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-113">If set to **No**, configure each IP address separately using the properties dialog box for each IP address.</span></span> <span data-ttu-id="b6e44-114">**예**로 설정된 경우 모든 IP 주소에 **IPAll** 속성 상자의 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-114">If set to **Yes**, the settings of the **IPAll** properties box will apply to all IP addresses.</span></span> <span data-ttu-id="b6e44-115">기본값은 **예**입니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-115">Default value is **Yes**.</span></span>  
  
 <span data-ttu-id="b6e44-116">**No Delay**</span><span class="sxs-lookup"><span data-stu-id="b6e44-116">**No Delay**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b6e44-117">는 이 속성에 대한 변경 내용을 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6e44-117">does not implement changes to this property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e44-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6e44-118">See Also</span></span>  
 <span data-ttu-id="b6e44-119">[네트워크 프로토콜 선택](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="b6e44-119">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="b6e44-120">TCP/IP를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="b6e44-120">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
