---
title: 공유 메모리 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6275215afdb6de3aa134dbffe74aa22b9e7b6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660232"
---
# <a name="shared-memory-properties"></a><span data-ttu-id="9bd70-102">공유 메모리 속성</span><span class="sxs-lookup"><span data-stu-id="9bd70-102">Shared Memory Properties</span></span>
  <span data-ttu-id="9bd70-103">**공유 메모리 속성**대화 상자의 **프로토콜** 페이지를 사용하여 공유 메모리 프로토콜을 활성화 또는 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd70-103">Use the **Protocol**page on the **Shared Memory Properties** dialog box to enable or disable the shared memory protocol.</span></span> <span data-ttu-id="9bd70-104">공유 메모리는 가장 간단한 프로토콜이며 구성 가능한 설정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd70-104">Shared memory is the simplest protocol to use and has no configurable settings.</span></span> <span data-ttu-id="9bd70-105">공유 메모리 프로토콜을 사용하는 클라이언트는 동일한 컴퓨터에서 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에만 연결할 수 있으므로 대부분의 데이터베이스 작업에 유용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd70-105">Because clients using the shared memory protocol can only connect to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance running on the same computer, it is not useful for most database activity.</span></span> <span data-ttu-id="9bd70-106">다른 프로토콜이 제대로 구성되지 않는 것으로 의심되는 경우 문제 해결에 공유 메모리 프로토콜을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="9bd70-106">Use the shared memory protocol for troubleshooting when you suspect the other protocols are configured incorrectly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9bd70-107">를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd70-107">must be restarted to enable or disable the protocol.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9bd70-108">옵션</span><span class="sxs-lookup"><span data-stu-id="9bd70-108">Options</span></span>  
 <span data-ttu-id="9bd70-109">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="9bd70-109">**Enabled**</span></span>  
 <span data-ttu-id="9bd70-110">가능한 값은 **예** 및 **아니요**입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd70-110">Possible values are **Yes** and **No**.</span></span> <span data-ttu-id="9bd70-111">공유 메모리 프로토콜은 기본적으로 활성화 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd70-111">The shared memory protocol is enabled by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd70-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bd70-112">See Also</span></span>  
 <span data-ttu-id="9bd70-113">[네트워크 프로토콜 선택](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="9bd70-113">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="9bd70-114">공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="9bd70-114">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
