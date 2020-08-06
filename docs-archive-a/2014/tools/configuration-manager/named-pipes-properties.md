---
title: 명명 된 파이프 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80790c1cb8830a0fd132721f375a70d2574421b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650333"
---
# <a name="named-pipes-properties"></a><span data-ttu-id="9fb5c-102">명명된 파이프 속성</span><span class="sxs-lookup"><span data-stu-id="9fb5c-102">Named Pipes Properties</span></span>
  <span data-ttu-id="9fb5c-103">명명된 파이프 프로토콜을 사용하는 경우 **명명된 파이프 속성** 대화 상자의 **프로토콜** 페이지를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 수신 대기하는 명명된 파이프를 보거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-103">Use the **Protocol**page on the **Named Pipes Properties** dialog box to view or change the named pipe that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens to, when using the Named Pipes protocol.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9fb5c-104">를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-104">must be restarted to enable or disable the protocol, or change the named pipe.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9fb5c-105">옵션</span><span class="sxs-lookup"><span data-stu-id="9fb5c-105">Options</span></span>  
 <span data-ttu-id="9fb5c-106">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="9fb5c-106">**Enabled**</span></span>  
 <span data-ttu-id="9fb5c-107">가능한 값은 **예** 및 **아니요**입니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-107">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="9fb5c-108">**파이프 이름**</span><span class="sxs-lookup"><span data-stu-id="9fb5c-108">**Pipe Name**</span></span>  
 <span data-ttu-id="9fb5c-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 수신 대기하는 명명된 파이프를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-109">Specifies the named pipe on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens.</span></span> <span data-ttu-id="9fb5c-110">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 은 기본 인스턴스의 경우 `\\.\pipe\sql\query` 에서 수신하고, 명명된 인스턴스의 경우 `\\.\pipe\MSSQL$<instancename>\sql\query` 에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-110">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query` for the default instance and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="9fb5c-111">이 필드는 2047자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-111">This field is limited to 2047 characters.</span></span>  
  
## <a name="creating-an-alternate-named-pipe"></a><span data-ttu-id="9fb5c-112">대체 명명된 파이프 만들기</span><span class="sxs-lookup"><span data-stu-id="9fb5c-112">Creating an Alternate Named Pipe</span></span>  
 <span data-ttu-id="9fb5c-113">명명된 파이프를 변경하려면 **파이프 이름** 입력란에 새 파이프 이름을 입력한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 중지하고 다시 시작하십시오.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-113">To change the named pipe, type the new pipe name in the **Pipe Name** box and then stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9fb5c-114">**sql\query** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용하는 명명된 파이프로 많이 알려졌으므로 파이프를 변경하면 악의적인 프로그램의 공격 위험을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-114">Since **sql\query** is well known as the named pipe used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], changing the pipe can help reduce the risk of attack by malicious programs.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9fb5c-115">예제</span><span class="sxs-lookup"><span data-stu-id="9fb5c-115">Example</span></span>  
 <span data-ttu-id="9fb5c-116">**\\\\.\pipe\unit\app** 을 입력하여 **unit\app** 파이프를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-116">Type **\\\\.\pipe\unit\app** to listen on the **unit\app** pipe.</span></span>  
  
 <span data-ttu-id="9fb5c-117">**\\\\.\pipe\acct** 를 입력하여 **acct** 파이프를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb5c-117">Type **\\\\.\pipe\acct** to listen on the **acct** pipe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb5c-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fb5c-118">See Also</span></span>  
 <span data-ttu-id="9fb5c-119">[서버 네트워크 프로토콜 설정 또는 해제](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="9fb5c-119">[Enable or Disable a Server Network Protocol](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 <span data-ttu-id="9fb5c-120">[네트워크 프로토콜 선택](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="9fb5c-120">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="9fb5c-121">명명된 파이프를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="9fb5c-121">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
