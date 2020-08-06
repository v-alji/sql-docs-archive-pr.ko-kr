---
title: sqlcmd 유틸리티 시작
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: rothja
ms.author: jroth
ms.openlocfilehash: d71e6f140238599b3f22850ee9b63a0ee25d900b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647574"
---
# <a name="start-the-sqlcmd-utility"></a><span data-ttu-id="59135-102">sqlcmd 유틸리티 시작</span><span class="sxs-lookup"><span data-stu-id="59135-102">Start the sqlcmd Utility</span></span>
  <span data-ttu-id="59135-103">`sqlcmd` 사용을 시작하려면 먼저 유틸리티를 시작한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-103">To begin using `sqlcmd`, you must first launch the utility and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="59135-104">기본 인스턴스나 명명된 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59135-104">You can connect to either a default or named instance.</span></span> <span data-ttu-id="59135-105">첫 번째 단계는 `sqlcmd` 유틸리티를 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="59135-105">The first step is to start the `sqlcmd` utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59135-106">`sqlcmd`에 대한 기본 인증 모드는 Windows 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="59135-106">Windows Authentication is the default authentication mode for `sqlcmd`.</span></span> <span data-ttu-id="59135-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하려면 **-U** 및 **-P** 옵션을 사용하여 사용자 이름과 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-107">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must specify a user name and password by using the **-U** and **-P** options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59135-108"> 기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 는 명명된 인스턴스인 **sqlexpress**로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="59135-108">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as the named instance **sqlexpress**.</span></span>  
  
 <span data-ttu-id="59135-109">이 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결한 적이 없는 경우 연결을 허용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 구성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59135-109">If you have not connected to this instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] before, you may have to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a><span data-ttu-id="59135-110">sqlcmd 유틸리티를 시작하여 SQL Server의 기본 인스턴스에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="59135-110">To start the sqlcmd utility and connect to a default instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="59135-111">**시작** 메뉴에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-111">On the **Start** menu click **Run**.</span></span> <span data-ttu-id="59135-112">**열기** 상자에 **cmd**를 입력한 다음 **확인** 을 클릭하여 명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="59135-112">In the **Open** box type **cmd**, and then click **OK** to open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="59135-113">명령 프롬프트에서 `sqlcmd`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-113">At the command prompt, type `sqlcmd`.</span></span>  
  
3.  <span data-ttu-id="59135-114">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="59135-114">Press ENTER.</span></span>  
  
     <span data-ttu-id="59135-115">이제 트러스트된 연결을 사용하여 컴퓨터에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 인스턴스에 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59135-115">You now have a trusted connection to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on your computer.</span></span>  
  
     <span data-ttu-id="59135-116">**1>** 은 `sqlcmd` 줄 번호를 지정 하는 프롬프트입니다.</span><span class="sxs-lookup"><span data-stu-id="59135-116">**1>** is the `sqlcmd` prompt that specifies the line number.</span></span> <span data-ttu-id="59135-117">Enter 키를 누를 때마다 번호가 1씩 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-117">Each time you press ENTER, the number increases by one.</span></span>  
  
4.  <span data-ttu-id="59135-118">세션을 종료 하려면 `sqlcmd` `EXIT` 프롬프트에을 입력 `sqlcmd` 합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-118">To end the `sqlcmd` session, type `EXIT` at the `sqlcmd` prompt.</span></span>  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="59135-119">sqlcmd 유틸리티를 시작하여 SQL Server의 명명된 인스턴스에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="59135-119">To start the sqlcmd utility and connect to a named instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="59135-120">명령 프롬프트 창을 열고 `sqlcmd -S` *myServer\instanceName*를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="59135-120">Open a Command Prompt window, and type `sqlcmd -S`*myServer\instanceName*.</span></span> <span data-ttu-id="59135-121">*myServer\instanceName* 을 연결하려는 컴퓨터 이름 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="59135-121">Replace *myServer\instanceName* with the name of the computer and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to.</span></span>  
  
2.  <span data-ttu-id="59135-122">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="59135-122">Press ENTER.</span></span>  
  
     <span data-ttu-id="59135-123">`sqlcmd`프롬프트 (1>)는 사용자가 지정 된 인스턴스에 연결 되었음을 나타냅니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="59135-123">The `sqlcmd` prompt (1>) indicates that you are connected to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="59135-124">입력한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 버퍼에 저장되며</span><span class="sxs-lookup"><span data-stu-id="59135-124">Entered [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are stored in a buffer.</span></span> <span data-ttu-id="59135-125">GO 명령이 발견되면 일괄 처리로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="59135-125">They are executed as a batch when the GO command is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59135-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59135-126">See Also</span></span>  
 [<span data-ttu-id="59135-127">sqlcmd를 사용하여 Transact-SQL 스크립트 파일 실행</span><span class="sxs-lookup"><span data-stu-id="59135-127">Run Transact-SQL Script Files Using sqlcmd</span></span>](sqlcmd-run-transact-sql-script-files.md)  
  
  
