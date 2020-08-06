---
title: 새 별칭 (별칭 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90742e5de3da0cac83c8b18eebba242ddb9a865d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650332"
---
# <a name="new-alias-alias-tab"></a><span data-ttu-id="ee18f-102">새 별칭(별칭 탭)</span><span class="sxs-lookup"><span data-stu-id="ee18f-102">New Alias (Alias Tab)</span></span>
  <span data-ttu-id="ee18f-103">별칭은 연결 설정에 사용할 수 있는 대체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-103">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="ee18f-104">별칭은 연결 문자열의 필수 요소를 캡슐화하고 사용자가 선택한 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-104">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="ee18f-105">**별칭 - 새로 만들기** 대화 상자의 **별칭** 페이지를 사용하여 별칭에 대한 연결 문자열의 요소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-105">Use the **Alias** page on the **Alias - New** dialog box to specify the elements of the connection string for an alias.</span></span> <span data-ttu-id="ee18f-106">기존 별칭의 연결 문자열을 변경하려면 [&#60;Alias&#62; 속성&#40;별칭 탭&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee18f-106">To change the connection string of an existing alias, see [&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md).</span></span>  
  
 <span data-ttu-id="ee18f-107">**속성** 표의 모든 값을 채울 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-107">All values in the **Properties** grid do not have to be completed.</span></span> <span data-ttu-id="ee18f-108">선택한 프로토콜에 따라 유효한 값 조합이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-108">Valid combinations vary depending on the protocol selected.</span></span> <span data-ttu-id="ee18f-109">유효한 값 조합의 예는 아래 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee18f-109">See the topics listed below for examples of valid combinations.</span></span>  
  
 <span data-ttu-id="ee18f-110">**별칭**</span><span class="sxs-lookup"><span data-stu-id="ee18f-110">**Alias Name**</span></span>  
 <span data-ttu-id="ee18f-111">이 연결을 나타내는 데 사용할 이름(별칭)입니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-111">The name (alias) that you want to use to refer to this connection.</span></span>  
  
 <span data-ttu-id="ee18f-112">**파이프 이름** / **포트 번호**</span><span class="sxs-lookup"><span data-stu-id="ee18f-112">**Pipe Name** / **Port No**</span></span>  
 <span data-ttu-id="ee18f-113">연결 문자열의 추가 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-113">Additional elements of the connection string.</span></span> <span data-ttu-id="ee18f-114">이 상자의 이름은 선택한 프로토콜에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-114">The name of this box varies with the selected protocol.</span></span>  
  
 <span data-ttu-id="ee18f-115">**프로토콜**</span><span class="sxs-lookup"><span data-stu-id="ee18f-115">**Protocol**</span></span>  
 <span data-ttu-id="ee18f-116">연결에 사용된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-116">The protocol used for the connection.</span></span>  
  
 <span data-ttu-id="ee18f-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="ee18f-117">**Server**</span></span>  
 <span data-ttu-id="ee18f-118">연결 중인 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-118">The name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance being connected to.</span></span>  
  
## <a name="when-to-use-an-alias"></a><span data-ttu-id="ee18f-119">별칭을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="ee18f-119">When to Use an Alias</span></span>  
 <span data-ttu-id="ee18f-120">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에 연결할 때는 **공유 메모리** 프로토콜을 사용하고 다른 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 때는 **TCP/IP** 또는 **명명된 파이프**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-120">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to a local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **Shared Memory** protocol, and to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on another computer using either **TCP/IP** or **Named Pipes**.</span></span> <span data-ttu-id="ee18f-121">TCP/IP 또는 명명된 파이프를 사용할 때, 사용자 지정 연결 문자열을 제공하려고 할 때 또는 연결에 대해 서버 이름 외에 다른 이름을 사용하려고 할 때 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-121">Create an alias when you are using TCP/IP or named pipes, and you want to provide a customized connection string, or when you want to use a name other than the server name for the connection.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ee18f-122">예</span><span class="sxs-lookup"><span data-stu-id="ee18f-122">Examples</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee18f-123">가 기본 TCP/IP 포트인 1433에서 수신하지 않고 다른 포트 번호를 사용하여 연결 문자열을 제공하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-123">is not listening on the default TCP/IP port of 1433 so you want to provide a connection string with a different port number.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee18f-124">가 기본 명명된 파이프에서 수신하지 않고 다른 파이프 이름을 사용하여 연결 문자열을 제공하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-124">is not listening on the default named pipe so you want to provide a connection string with a different pipe name.</span></span>  
  
-   <span data-ttu-id="ee18f-125">애플리케이션이 서버의 `ACCT`라는 데이터베이스에 연결하려고 하는데 이 데이터베이스가 `ACCT` 이라는 서버의 `CENTRAL`라는 인스턴스로 통합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-125">An application expects to connect to a database on the server named `ACCT`, but that database has been consolidated as an instance named `ACCT` on a server named `CENTRAL`.</span></span> <span data-ttu-id="ee18f-126">애플리케이션은 쉽게 변경할 수 없으므로</span><span class="sxs-lookup"><span data-stu-id="ee18f-126">The application cannot easily be changed.</span></span> <span data-ttu-id="ee18f-127">`ACCT`를 가리키는 문자열을 사용하여 `CENTRAL\ACCT`라는 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee18f-127">Create an alias named `ACCT`, with a connection string pointing to `CENTRAL\ACCT`.</span></span>  
  
## <a name="creating-a-valid-connection-string"></a><span data-ttu-id="ee18f-128">유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="ee18f-128">Creating a Valid Connection String</span></span>  
 <span data-ttu-id="ee18f-129">유효한 별칭 속성 조합에 대한 설명과 예는 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee18f-129">See the following topics for a description and examples of valid combinations of alias properties:</span></span>  
  
-   [<span data-ttu-id="ee18f-130">공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="ee18f-130">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [<span data-ttu-id="ee18f-131">TCP/IP를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="ee18f-131">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [<span data-ttu-id="ee18f-132">명명된 파이프를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="ee18f-132">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
