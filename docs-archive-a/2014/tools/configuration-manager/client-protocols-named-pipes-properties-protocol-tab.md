---
title: 클라이언트 프로토콜 - 명명된 파이프 속성(프로토콜 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: stevestein
ms.author: sstein
ms.openlocfilehash: 169b6d98212c724b8d6c43615ae2fa7eba9cfc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728999"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a><span data-ttu-id="d0317-102">클라이언트 프로토콜 - 명명된 파이프 속성(프로토콜 탭)</span><span class="sxs-lookup"><span data-stu-id="d0317-102">Client Protocols - Named Pipes Properties (Protocol Tab)</span></span>
  <span data-ttu-id="d0317-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **명명된 파이프 속성** 대화 상자의 **프로토콜** 탭을 사용하여 기본 파이프에 대한 설명을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0317-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager use the **Protocol** tab on the **Named Pipes Properties** dialog box to view or modify the description of default pipe.</span></span> <span data-ttu-id="d0317-104">다른 파이프에 연결하려면 **기본 파이프** 상자에 해당 파이프를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0317-104">To connect to a different pipe, type the pipe in the **Default Pipe** box.</span></span> <span data-ttu-id="d0317-105">연결 문자열에 대한 자세한 내용은 [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0317-105">For more information about connection strings, see [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0317-106">옵션</span><span class="sxs-lookup"><span data-stu-id="d0317-106">Options</span></span>  
 <span data-ttu-id="d0317-107">**기본 파이프**</span><span class="sxs-lookup"><span data-stu-id="d0317-107">**Default Pipe**</span></span>  
 <span data-ttu-id="d0317-108">대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결할 때 명명된 파이프 Net-library가 사용할 기본 파이프를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0317-108">Specifies the default pipe the Named Pipes Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d0317-109">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 `\\.\pipe\sql\query`</span><span class="sxs-lookup"><span data-stu-id="d0317-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query`</span></span>  
  
 <span data-ttu-id="d0317-110">기본 파이프에 연결하려면 `sql\query`</span><span class="sxs-lookup"><span data-stu-id="d0317-110">To connect to the default pipe, enter `sql\query`</span></span>  
  
 <span data-ttu-id="d0317-111">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d0317-111">**Enabled**</span></span>  
 <span data-ttu-id="d0317-112">가능한 값은 **예** 및 **아니요**입니다.</span><span class="sxs-lookup"><span data-stu-id="d0317-112">Possible values are **Yes** and **No**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0317-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0317-113">See Also</span></span>  
 [<span data-ttu-id="d0317-114">네트워크 프로토콜 선택</span><span class="sxs-lookup"><span data-stu-id="d0317-114">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
