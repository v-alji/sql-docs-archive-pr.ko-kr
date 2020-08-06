---
title: 트랜잭션 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a075719c8ed31ffcc1c34f2d013a8beb0ae40dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652060"
---
# <a name="using-transactions"></a><span data-ttu-id="186bf-102">트랜잭션 사용</span><span class="sxs-lookup"><span data-stu-id="186bf-102">Using Transactions</span></span>
  <span data-ttu-id="186bf-103">SMO([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Object)에서 트랜잭션 처리는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="186bf-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), transaction processing is achieved through the connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span> <span data-ttu-id="186bf-104"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 연결이 설정 되 면 개체의 속성에서 개체를 참조 합니다 <xref:Microsoft.SqlServer.Management.Smo.Server> .</span><span class="sxs-lookup"><span data-stu-id="186bf-104">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object is referenced by the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object when the connection is established.</span></span> <span data-ttu-id="186bf-105"><xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> 및 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>과 같은 메서드는 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 개체 속성에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="186bf-105">Methods such as <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>, and <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> belong to the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="186bf-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="186bf-106">See Also</span></span>  
 [<span data-ttu-id="186bf-107">SMO 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="186bf-107">Creating SMO Programs</span></span>](creating-smo-programs.md)  
  
  
