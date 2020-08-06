---
title: 인터넷을 통한 복제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46c61f8a5383c87d46fa0dbda18876b43ffb7739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646322"
---
# <a name="replication-over-the-internet"></a><span data-ttu-id="4cc09-102">인터넷을 통한 복제</span><span class="sxs-lookup"><span data-stu-id="4cc09-102">Replication over the Internet</span></span>
  <span data-ttu-id="4cc09-103">인터넷으로 데이터를 복제하면 연결이 끊긴 원격 사용자가 필요할 때 인터넷 연결을 사용해서 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc09-103">Replicating data over the Internet allows remote, disconnected users to access data when they need it using a connection to the Internet.</span></span> <span data-ttu-id="4cc09-104">다음을 사용하여 인터넷을 통해 데이터를 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc09-104">Replicate data over the Internet using:</span></span>  
  
-   <span data-ttu-id="4cc09-105">VPN(가상 프라이빗 네트워크).</span><span class="sxs-lookup"><span data-stu-id="4cc09-105">A Virtual Private Network (VPN).</span></span> <span data-ttu-id="4cc09-106">자세한 내용은 [VPN을 사용하여 인터넷을 통해 데이터 게시](publish-data-over-the-internet-using-vpn.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cc09-106">For more information, see [Publish Data over the Internet Using VPN](publish-data-over-the-internet-using-vpn.md).</span></span>  
  
-   <span data-ttu-id="4cc09-107">병합 복제를 위한 웹 동기화 옵션.</span><span class="sxs-lookup"><span data-stu-id="4cc09-107">The Web synchronization option for merge replication.</span></span> <span data-ttu-id="4cc09-108">자세한 내용은 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cc09-108">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="4cc09-109">모든 유형의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 시 VPN을 통해 데이터를 복제할 수 있지만 병합 복제를 사용할 경우 웹 동기화를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc09-109">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but you should consider Web synchronization if you are using merge replication.</span></span>  
  
  
