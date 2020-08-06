---
title: Data Quality Client 애플리케이션 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45372ce22fd1b18f0ec13f7a7fd76a369b78dfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742611"
---
# <a name="run-the-data-quality-client-application"></a><span data-ttu-id="c9dac-102">데이터 품질 클라이언트 애플리케이션 실행</span><span class="sxs-lookup"><span data-stu-id="c9dac-102">Run the Data Quality Client Application</span></span>
  <span data-ttu-id="c9dac-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]를 실행하고 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]에 로그온하면 DQS([!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)])를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-103">You can use [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by running [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and logging on to a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c9dac-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c9dac-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c9dac-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="c9dac-105">Prerequisites</span></span>  
 <span data-ttu-id="c9dac-106">DQSInstaller.exe 파일을 실행하여 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 설치를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-106">You must have completed the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="c9dac-107">자세한 내용은 [DQSInstaller.exe를 실행하여 Data Quality 서버 설치 완료](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9dac-107">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c9dac-108">보안</span><span class="sxs-lookup"><span data-stu-id="c9dac-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c9dac-109">권한</span><span class="sxs-lookup"><span data-stu-id="c9dac-109">Permissions</span></span>  
 <span data-ttu-id="c9dac-110">DQS_MAIN 데이터베이스에 대해 세 가지 DQS 역할(dqs_adminstrator, dqs_kb_editor 또는 dqs_kb_operator) 중 하나가 있어야 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]에 로그온할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-110">You must have one of the three DQS roles (dqs_adminstrator, dqs_kb_editor, or dqs_kb_operator) granted on the DQS_MAIN database to be able to log on to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a><span data-ttu-id="c9dac-111">Data Quality Client 실행</span><span class="sxs-lookup"><span data-stu-id="c9dac-111">Run Data Quality Client</span></span>  
 <span data-ttu-id="c9dac-112">설치된 컴퓨터에서 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]를 실행하려면 다음과 같이 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-112">To run [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] on the computer where you have installed it, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="c9dac-113">**시작**을 클릭하고 **모든 프로그램**을 가리킨 다음 **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, **Data Quality Services**, **Data Quality 클라이언트**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-113">Click **Start**, point to **All Programs**, click **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="c9dac-114">**서버에 연결** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-114">In the **Connect to Server** dialog box:</span></span>  
  
    1.  <span data-ttu-id="c9dac-115">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션을 연결할 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-115">Specify the server that you want to connect the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application to.</span></span> <span data-ttu-id="c9dac-116">**(로컬)** 을 선택하여 로컬 컴퓨터의 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-116">Select **(LOCAL)** to connect to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] on the local computer.</span></span> <span data-ttu-id="c9dac-117">아래쪽 화살표를 클릭 하 고 **\<Browse network for more servers>** 를 선택 하 여 다른 서버에 연결 하거나 이름으로 로컬 서버에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-117">You can also click the down arrow and select **\<Browse network for more servers>** to connect to a different server (or to connect to the local server by name).</span></span> <span data-ttu-id="c9dac-118">**서버 찾아보기** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-118">The **Browse for Servers** dialog box will be displayed.</span></span> <span data-ttu-id="c9dac-119">**로컬 서버** 탭이나 **네트워크 서버** 탭에서 서버를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-119">You can select a server in the **Local Servers** tab or in the **Network Servers** tab.</span></span>  
  
    2.  <span data-ttu-id="c9dac-120">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]와 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 사이의 데이터 전송을 암호화하려면 **옵션**을 클릭하고 **연결 암호화** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-120">If you want to encrypt data transfer between [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], click **Options**, and then select the **Encrypt Connection** check box.</span></span>  
  
3.  <span data-ttu-id="c9dac-121">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-121">Click **Connect**.</span></span>  
  
 <span data-ttu-id="c9dac-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c9dac-122">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen appears.</span></span> <span data-ttu-id="c9dac-123">자세한 내용은 [데이터 품질 클라이언트 홈 화면](../../2014/data-quality-services/data-quality-client-home-screen.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9dac-123">For more information, see [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md).</span></span>  
  
  
