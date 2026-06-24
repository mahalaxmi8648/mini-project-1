import React, { useState } from "react";

function App() {
  const [isSignup, setIsSignup] = useState(true);
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const [student, setStudent] = useState({
    name: "",
    rollNo: "",
    course: "",
    email: "",
    password: "",
  });

  const [loginData, setLoginData] = useState({
    email: "",
    password: "",
  });

  const handleSignup = (e) => {
    e.preventDefault();
    alert("Signup Successful");
    setIsSignup(false);
  };

  const handleLogin = (e) => {
    e.preventDefault();

    if (
      loginData.email === student.email &&
      loginData.password === student.password
    ) {
      setIsLoggedIn(true);
    } else {
      alert("Invalid Credentials");
    }
  };

  const handleLogout = () => {
    setIsLoggedIn(false);
    setIsSignup(false);
  };

  return (
    <div style={styles.container}>
      <div style={styles.card}>
        {!isLoggedIn ? (
          isSignup ? (
            <>
              <h1 style={styles.title}>Student Signup</h1>

              <form onSubmit={handleSignup}>
                <input
                  type="text"
                  placeholder="Name"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setStudent({ ...student, name: e.target.value })
                  }
                />

                <input
                  type="text"
                  placeholder="Roll No"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setStudent({ ...student, rollNo: e.target.value })
                  }
                />

                <input
                  type="text"
                  placeholder="Course"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setStudent({ ...student, course: e.target.value })
                  }
                />

                <input
                  type="email"
                  placeholder="Email"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setStudent({ ...student, email: e.target.value })
                  }
                />

                <input
                  type="password"
                  placeholder="Password"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setStudent({ ...student, password: e.target.value })
                  }
                />

                <button type="submit" style={styles.button}>
                  Signup
                </button>
              </form>

              <p style={styles.text}>
                Already have an account?{" "}
                <span
                  style={styles.link}
                  onClick={() => setIsSignup(false)}
                >
                  Login
                </span>
              </p>
            </>
          ) : (
            <>
              <h1 style={styles.title}>Student Login</h1>

              <form onSubmit={handleLogin}>
                <input
                  type="email"
                  placeholder="Email"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setLoginData({
                      ...loginData,
                      email: e.target.value,
                    })
                  }
                />

                <input
                  type="password"
                  placeholder="Password"
                  style={styles.input}
                  required
                  onChange={(e) =>
                    setLoginData({
                      ...loginData,
                      password: e.target.value,
                    })
                  }
                />

                <button type="submit" style={styles.button}>
                  Login
                </button>
              </form>

              <p style={styles.text}>
                Don't have an account?{" "}
                <span
                  style={styles.link}
                  onClick={() => setIsSignup(true)}
                >
                  Signup
                </span>
              </p>
            </>
          )
        ) : (
          <>
            <h1 style={styles.title}>Student Dashboard</h1>

            <h2 style={styles.welcome}>
              Welcome {student.name}
            </h2>

            <p style={styles.info}>
              <strong>Roll No:</strong> {student.rollNo}
            </p>

            <p style={styles.info}>
              <strong>Course:</strong> {student.course}
            </p>

            <p style={styles.info}>
              <strong>Email:</strong> {student.email}
            </p>

            <button style={styles.button} onClick={handleLogout}>
              Logout
            </button>
          </>
        )}
      </div>
    </div>
  );
}

const styles = {
  container: {
    minHeight: "100vh",
    display: "flex",
    justifyContent: "center",
    alignItems: "center",
    backgroundColor: "#eef3ff",
  },

  card: {
    width: "450px",
    background: "#fff",
    padding: "35px",
    borderRadius: "15px",
    boxShadow: "0 4px 15px rgba(0,0,0,0.15)",
  },

  title: {
    textAlign: "center",
    marginBottom: "25px",
    fontSize: "40px",
  },

  input: {
    width: "100%",
    padding: "12px",
    marginBottom: "15px",
    border: "1px solid #ccc",
    borderRadius: "5px",
    boxSizing: "border-box",
  },

  button: {
    width: "100%",
    padding: "12px",
    backgroundColor: "#1d4ed8",
    color: "#fff",
    border: "none",
    borderRadius: "5px",
    cursor: "pointer",
    fontSize: "16px",
  },

  text: {
    textAlign: "center",
    marginTop: "15px",
  },

  link: {
    color: "#1d4ed8",
    cursor: "pointer",
    fontWeight: "bold",
  },

  welcome: {
    textAlign: "center",
    marginBottom: "20px",
  },

  info: {
    textAlign: "center",
    fontSize: "18px",
    margin: "12px 0",
  },
};

export default App;
