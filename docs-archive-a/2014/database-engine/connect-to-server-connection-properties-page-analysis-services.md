---
title: 서버에 연결(연결 속성 페이지) Analysis Services | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoas.connectionproperties.f1
ms.assetid: 26cf53e3-3bcb-4697-8a88-53e93bc68b56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 04706671ea8b0a50f2bf72cd7b73db88dce34d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727339"
---
# <a name="connect-to-server-connection-properties-page-analysis-services"></a><span data-ttu-id="b7778-102">서버에 연결(연결 속성 페이지) Analysis Services</span><span class="sxs-lookup"><span data-stu-id="b7778-102">Connect to Server (Connection Properties Page) Analysis Services</span></span>
  <span data-ttu-id="b7778-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssAS](../includes/ssas-md.md)] **등록 된 서버에 연결 하거나 등록 된 서버**에 등록할 때이 탭을 사용 하 여 옵션을 확인 하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] or registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="b7778-104">**연결** 및 **옵션** 은 연결 시에만 이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="b7778-105">**테스트** 및 **저장** 은 [!INCLUDE[ssAS](../includes/ssas-md.md)]등록 시에만 이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssAS](../includes/ssas-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="b7778-106">옵션</span><span class="sxs-lookup"><span data-stu-id="b7778-106">Options</span></span>  
 <span data-ttu-id="b7778-107">**데이터베이스에 연결**</span><span class="sxs-lookup"><span data-stu-id="b7778-107">**Connect to database**</span></span>  
 <span data-ttu-id="b7778-108">목록에서 연결할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="b7778-109">를 선택 하면 **\<default>** 서버의 기본 데이터베이스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="b7778-110">를 선택 하면 **\<Browse server>** 연결 하려는 데이터베이스에 대 한 서버를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-110">If you select **\<Browse server>**, you can browse the server for the database you would like to connect to.</span></span>  
  
 <span data-ttu-id="b7778-111">**연결 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="b7778-111">**Connection timeout**</span></span>  
 <span data-ttu-id="b7778-112">제한 시간이 초과 되기 전까지 연결이 설정 될 때까지 대기 하는 시간 (초)을 입력 합니다. 기본값은 15 초입니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-112">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="b7778-113">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="b7778-113">**Execution timeout**</span></span>  
 <span data-ttu-id="b7778-114">서버에서 태스크가 실행 완료되기까지 대기하는 시간(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-114">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="b7778-115">기본값은 0초이며 시간 제한 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-115">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="b7778-116">**연결 암호화**</span><span class="sxs-lookup"><span data-stu-id="b7778-116">**Encrypt connection**</span></span>  
 <span data-ttu-id="b7778-117">연결 암호화를 강제 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-117">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="b7778-118">**모두 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="b7778-118">**Reset All**</span></span>  
 <span data-ttu-id="b7778-119">수동으로 입력한 모든 연결 속성 값을 기본값으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-119">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="b7778-120">**연결**</span><span class="sxs-lookup"><span data-stu-id="b7778-120">**Connect**</span></span>  
 <span data-ttu-id="b7778-121">목록에 있는 값을 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-121">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="b7778-122">**Options**</span><span class="sxs-lookup"><span data-stu-id="b7778-122">**Options**</span></span>  
 <span data-ttu-id="b7778-123">대화 상자를 변경하고 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-123">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="b7778-124">**Test**</span><span class="sxs-lookup"><span data-stu-id="b7778-124">**Test**</span></span>  
 <span data-ttu-id="b7778-125">[!INCLUDE[ssAS](../includes/ssas-md.md)] 을 **등록된 서버**에 등록하는 경우 연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-125">When registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="b7778-126">**저장**</span><span class="sxs-lookup"><span data-stu-id="b7778-126">**Save**</span></span>  
 <span data-ttu-id="b7778-127">**등록된 서버**에 설정을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b7778-127">Saves the settings in **Registered Servers**.</span></span>  
  
  
