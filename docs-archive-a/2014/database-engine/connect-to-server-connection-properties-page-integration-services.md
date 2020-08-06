---
title: 서버에 연결 (연결 속성 페이지) Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodts.connectionproperties.f1
- sql12.ssiseditserverregistration.connectionproperties.f1
ms.assetid: c2513dab-8415-4e0c-9475-6d4ab97fea7c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 05f3d370a3f3a299bb90df53538b3fa3e90e28c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740377"
---
# <a name="connect-to-server-connection-properties-page-integration-services"></a><span data-ttu-id="cb5f9-102">서버에 연결(연결 속성 페이지) Integration Services</span><span class="sxs-lookup"><span data-stu-id="cb5f9-102">Connect to Server (Connection Properties Page) Integration Services</span></span>
  <span data-ttu-id="cb5f9-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssIS](../includes/ssis-md.md)] **등록 된 서버에 연결 하거나 등록 된 서버**에 등록할 때이 탭을 사용 하 여 옵션을 확인 하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] or registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="cb5f9-104">**연결** 및 **옵션** 은 연결 시에만 이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="cb5f9-105">**테스트** 및 **저장** 은 [!INCLUDE[ssIS](../includes/ssis-md.md)]등록 시에만 이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="cb5f9-106">옵션</span><span class="sxs-lookup"><span data-stu-id="cb5f9-106">Options</span></span>  
 <span data-ttu-id="cb5f9-107">**포트 번호**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-107">**Port number**</span></span>  
 <span data-ttu-id="cb5f9-108">[!INCLUDE[ssIS](../includes/ssis-md.md)]에서 사용하는 포트 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-108">Enter the port number used by [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="cb5f9-109">**연결 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-109">**Connection time-out**</span></span>  
 <span data-ttu-id="cb5f9-110">제한 시간이 초과 되기 전까지 연결이 설정 될 때까지 대기 하는 시간 (초)을 입력 합니다. 기본값은 15 초입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-110">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="cb5f9-111">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-111">**Execution time-out**</span></span>  
 <span data-ttu-id="cb5f9-112">서버에서 태스크가 실행 완료되기까지 대기하는 시간(초)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-112">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="cb5f9-113">기본값은 0초이며 시간 제한 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-113">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="cb5f9-114">**모두 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-114">**Reset All**</span></span>  
 <span data-ttu-id="cb5f9-115">수동으로 입력한 모든 연결 속성 값을 기본값으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-115">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="cb5f9-116">**연결**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-116">**Connect**</span></span>  
 <span data-ttu-id="cb5f9-117">목록에 있는 값을 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-117">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="cb5f9-118">**Options**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-118">**Options**</span></span>  
 <span data-ttu-id="cb5f9-119">대화 상자를 변경하고 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-119">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="cb5f9-120">**Test**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-120">**Test**</span></span>  
 <span data-ttu-id="cb5f9-121">[!INCLUDE[ssIS](../includes/ssis-md.md)] 을 **등록된 서버**에 등록하는 경우 연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-121">When registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="cb5f9-122">**저장**</span><span class="sxs-lookup"><span data-stu-id="cb5f9-122">**Save**</span></span>  
 <span data-ttu-id="cb5f9-123">**등록된 서버**에 설정을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5f9-123">Saves the settings in **Registered Servers**.</span></span>  
  
  
