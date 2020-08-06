---
title: 프록시 서버를 통해 SQL Server에 연결 (SQL Server 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: de22ad6043c509f08471a6bea40c0efa18d76842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652323"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a><span data-ttu-id="0edad-102">프록시 서버를 통해 SQL Server에 연결(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="0edad-102">Connect to SQL Server Through a Proxy Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="0edad-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 프록시 서버를 통해 SQL Server에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0edad-103">This topic describes how to connect to SQL Server through a proxy server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="0edad-104">원격 WinSock(RWS)를 통해 원격으로 수신하려면 수신 노드 주소가 LAT 항목의 범위 밖에 있도록 프록시 서버에 대해 로컬 주소 테이블(LAT)을 정의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0edad-104">To listen remotely by way of Remote WinSock (RWS), define the local address table (LAT) for the proxy server so that the listening node address is outside the range of LAT entries.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0edad-105">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="0edad-105">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a><span data-ttu-id="0edad-106">Microsoft Proxy Server를 통해 SQL Server에 대한 연결을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="0edad-106">To enable connections to SQL Server through Microsoft Proxy Server</span></span>  
  
1.  <span data-ttu-id="0edad-107">[특정 TCP 포트로 수신하도록 서버 구성&#40;SQL Server 구성 관리자&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md)의 단계에 따라 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 사용하는 TCP/IP 포트를 확인하거나 원하는 포트를 사용하도록 [!INCLUDE[ssDE](../../includes/ssde-md.md)]를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0edad-107">Follow the steps in [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md) to determine which TCP/IP ports are used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to use a desired port.</span></span>  
  
2.  <span data-ttu-id="0edad-108">사용 중인 프록시 서버에서 수신 노드 주소가 LAT(로컬 주소 테이블) 항목의 범위 밖에 있도록 프록시 서버에 LAT를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0edad-108">In your proxy server define the local address table (LAT) for the proxy server so that the listening node address is outside the range of LAT entries.</span></span> <span data-ttu-id="0edad-109">자세한 내용은 프록시 서버 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0edad-109">For more information, see your proxy server documentation.</span></span>  
  
  
