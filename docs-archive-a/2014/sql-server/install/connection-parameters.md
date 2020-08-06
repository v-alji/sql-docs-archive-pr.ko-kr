---
title: 연결 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27eb69dfd2c41710a47861e0992486267f692a3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648780"
---
# <a name="connection-parameters"></a><span data-ttu-id="340f0-102">연결 매개 변수</span><span class="sxs-lookup"><span data-stu-id="340f0-102">Connection Parameters</span></span>
  <span data-ttu-id="340f0-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]과 같은 특정 서버 유형을 분석하려면 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-103">To analyze certain server types, such as the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], you must select a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="340f0-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-104">The default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is automatically selected.</span></span> <span data-ttu-id="340f0-105">이 선택 항목을 변경할 수 있지만 업그레이드 관리자에서 분석할 인스턴스는 한 번에 하나만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-105">You can change this selection, but you can select only one instance at a time for analysis by Upgrade Advisor.</span></span> <span data-ttu-id="340f0-106">인증이 필요한 서버 유형을 포함한 경우 인증 모드와 자격 증명을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-106">If you have included a server type that requires authentication, you must enter the authentication mode and credentials.</span></span>  
  
## <a name="options"></a><span data-ttu-id="340f0-107">옵션</span><span class="sxs-lookup"><span data-stu-id="340f0-107">Options</span></span>  
 <span data-ttu-id="340f0-108">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="340f0-108">**Server name**</span></span>  
 <span data-ttu-id="340f0-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소 창에 입력한 컴퓨터 이름으로 미리 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-109">Pre-populated with the computer name that you entered in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components pane.</span></span>  
  
 <span data-ttu-id="340f0-110">**인스턴스 이름**</span><span class="sxs-lookup"><span data-stu-id="340f0-110">**Instance name**</span></span>  
 <span data-ttu-id="340f0-111">컴퓨터에서 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-111">Select from the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are available on the computer.</span></span> <span data-ttu-id="340f0-112">인스턴스 목록이 표시되지 않으면 MSSQLSERVER를 사용하여 기본 인스턴스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-112">If you do not see a list of instances, use MSSQLSERVER to scan the default instance.</span></span> <span data-ttu-id="340f0-113">이 작업은 원격 컴퓨터와 특히 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-113">This is especially relevant for remote computers.</span></span> <span data-ttu-id="340f0-114">"default"라는 단어를 사용하여 기본 인스턴스를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-114">You can also use the word "default" to scan the default instance.</span></span>  
  
 <span data-ttu-id="340f0-115">**인증**</span><span class="sxs-lookup"><span data-stu-id="340f0-115">**Authentication**</span></span>  
 <span data-ttu-id="340f0-116">이 컴퓨터에서 사용할 수 있는 인증 모드 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-116">Select from the list of available authentication modes on this computer.</span></span> <span data-ttu-id="340f0-117">기본 인증 모드는 Windows 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-117">By default, the authentication mode is Windows Authentication.</span></span>  
  
 <span data-ttu-id="340f0-118">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="340f0-118">**User name**</span></span>  
 <span data-ttu-id="340f0-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 이 상자에 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-119">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, enter a user name in the box.</span></span> <span data-ttu-id="340f0-120">컴퓨터에 대한 관리자 자격 증명이 있는 사용자 이름을 입력하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-120">We recommend that the user name have administrative credentials on the computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="340f0-121">Windows 인증을 선택 하는 경우 현재 로그온 한 사용자의 사용자 이름이 **사용자 이름** 텍스트 상자에 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-121">If you select Windows Authentication, the user name of the currently logged-on user is populated in the **User name** text box.</span></span>  
  
 <span data-ttu-id="340f0-122">**암호**</span><span class="sxs-lookup"><span data-stu-id="340f0-122">**Password**</span></span>  
 <span data-ttu-id="340f0-123">지정된 사용자의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="340f0-123">Enter the password for the specified user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="340f0-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="340f0-124">See Also</span></span>  
 <span data-ttu-id="340f0-125">[업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="340f0-125">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="340f0-126">업그레이드 관리자 사용자 인터페이스 참조</span><span class="sxs-lookup"><span data-stu-id="340f0-126">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
